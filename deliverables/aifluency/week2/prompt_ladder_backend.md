# Prompt Ladder: "Write Backend Code"

**Track:** Backend engineering (FastAPI)
**Why this prompt:** "Write backend code" is a prompt I'd have typed a month ago without thinking twice — vague on purpose, to expose exactly how much a lazy prompt costs.

---

## Baseline (embarrassing, on purpose)

**Prompt:**
> "Write backend code for authentication."

**Output (representative excerpt):**
```python
def login(username, password):
    user = get_user(username)
    if user and user.password == password:
        return "Login successful"
    else:
        return "Login failed"
```

**Why it's weak:** It's not tied to any framework, stores/compares passwords in plaintext, returns a string instead of a real response, and would fail instantly in any real codebase. It's the kind of answer that "looks like code" but isn't usable by anyone.

---

## Version 1 — Add a clearer goal

**Layer added:** a concrete goal (not "authentication" in the abstract — a specific working endpoint)

**Prompt:**
> "Write a FastAPI endpoint that logs a user in and returns a JWT access token on success."

**What changed in the prompt:** Replaced the vague noun "authentication" with a named framework and a named deliverable (a working endpoint returning a token).

**What actually improved in the output:** The code became runnable — it used `@app.post("/login")`, imported `jwt`, and returned an actual `{"access_token": ...}` response instead of a string. It stopped being pseudocode.

**What still failed:** Passwords were still compared with plain `==`, and there was no hashing. A goal alone doesn't teach it my security standards — it just teaches it my framework.

**What I'd try next:** Give it the real context of the system it needs to fit into.

---

## Version 2 — Add real context

**Layer added:** the actual system (existing stack, existing table shape, existing conventions)

**Prompt:**
> "Write a FastAPI endpoint that logs a user in and returns a JWT access token on success. Context: the project uses SQLAlchemy with a `User` model that has a `hashed_password` column (bcrypt via `passlib`), and every other route in the project returns errors as `{"error": "message"}` with the matching HTTP status code, not a generic 401 with no body."

**What changed in the prompt:** Added two sentences describing the real database model and the project's existing error-handling convention.

**What actually improved in the output:** Password comparison switched to `pwd_context.verify(password, user.hashed_password)` instead of `==`, and failure responses matched the project's actual error shape: `JSONResponse(status_code=401, content={"error": "Invalid credentials"})`. This is the first version that would blend into an existing codebase instead of looking bolted on.

**What still failed:** It returned `{"error": "Invalid credentials"}` for both "user doesn't exist" and "wrong password" — which is actually *correct* for security, but it did that by accident, not because I asked for it. A future version needs to make that intentional, not lucky.

**What I'd try next:** Add explicit constraints instead of relying on the model to guess the security-sensitive parts right.

---

## Version 3 — Add constraints

**Layer added:** explicit, non-negotiable rules

**Prompt:**
> [Same as Version 2, plus:] "Constraints: never reveal whether the failure was 'user not found' or 'wrong password' — both must return the identical error message and status code. Never log the raw password, even at debug level. Rate-limiting is out of scope for this endpoint — don't add it."

**What changed in the prompt:** Added three explicit rules — one security rule to enforce, one to prohibit, and one deliberate scope boundary.

**What actually improved in the output:** The identical-error behavior from V2 became explicit and commented (`# Same error for both cases — do not leak which one failed`), which matters because now it's a documented decision, not an accident a future editor might "fix" into a leak. It also dropped a debug `print(password)` line that had quietly been in V2's output the whole time — I hadn't even noticed it until I told the model not to do it.

**What still failed:** Telling it rate-limiting was "out of scope" caused it to add a comment explaining *why* rate limiting wasn't included, unprompted — a small but real instance of the model over-explaining a boundary I only meant to set, not justify.

**What I'd try next:** Tighten the output format so it stops adding unrequested commentary.

---

## Version 4 — Add a specified output format (the one that backfired)

**Layer added:** a strict format — code only, no prose, no comments outside the function

**Prompt:**
> [Same as Version 3, plus:] "Output ONLY the final code. No explanation before or after. No inline comments."

**What changed in the prompt:** Explicitly banned prose and comments.

**What actually improved in the output:** It got shorter and pasted cleanly into a file with zero editing.

**What still failed — this is the honest "made it worse" moment:** Removing the comment that said *"# Same error for both cases — do not leak which one failed"* was a real loss. That comment was the one thing in V3 protecting the security decision from being "cleaned up" by someone later who didn't know it was intentional. Banning comments entirely to get clean output also deleted the one piece of institutional memory the code needed. **A blanket "no comments" rule optimized for the wrong thing — pasteability over safety.**

**What I'd try next:** Ban prose *around* the code, but require exactly one comment on any line that isn't self-explanatory from a security standpoint.

---

## Version 5 — Add a verification requirement

**Layer added:** a targeted self-check, replacing V4's blanket ban

**Prompt:**
> [Same as Version 3, plus:] "Output the code with no explanation before or after it. The only comments allowed are ones that explain a security-relevant decision a future editor might otherwise 'simplify' by mistake — for example, why both failure cases return an identical error. Do not comment on anything else."

**What changed in the prompt:** Replaced the all-or-nothing comment ban with a narrow, reasoned rule: comments are earned, not banned.

**What actually improved in the output:** The identical-error line got its protective comment back, and nothing else did — no over-explaining the rate-limiting boundary, no restating what the code obviously does. This is the first version that is both clean *and* safe to hand to someone else without a walkthrough.

**What still failed:** Nothing new broke, but this version took real iteration to phrase precisely — "comments are earned, not banned" is a harder instruction to write than either extreme, which is itself worth noting: the middle ground cost more effort than either the blanket ban or no rule at all.

---

## Final Reusable Prompt

Cleaned up so a stranger on this track could use it for any backend endpoint, not just this one:

> "Write a [FRAMEWORK] endpoint that [SPECIFIC BEHAVIOR AND SUCCESS RESPONSE]. Context: the project uses [REAL STACK / MODEL SHAPE / EXISTING CONVENTIONS]. Constraints: [SECURITY OR CORRECTNESS RULES THAT ARE NON-NEGOTIABLE]. Explicitly out of scope: [WHAT NOT TO ADD]. Output only the final code, no prose before or after. The only comments allowed are ones explaining a decision a future editor might accidentally 'simplify' into a bug — comment nothing else."

**Why this version, and not V4's total silence:** the format rule that survived wasn't "no comments" — it was "only comments that protect a decision." Silence looked cleaner in isolation, but it deleted the one piece of information that kept the code safe.

---

## Summary Table

| Version | Layer added | Net effect |
|---|---|---|
| Baseline | — | Unrunnable pseudocode, plaintext password comparison |
| V1 | Clearer goal | Became real, framework-specific, runnable code |
| V2 | Real context | Matched existing DB model and error conventions |
| V3 | Constraints | Made a security decision explicit and caught a stray debug leak |
| V4 | Output format (blanket ban) | **Backfired** — deleted the one comment protecting a security decision |
| V5 | Verification requirement | Restored the protective comment, cut everything else |
