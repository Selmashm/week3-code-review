# Review Log – `write-pr-description`

**Skill reviewed:** `skills/write-pr-description/SKILL.md`
**Reviewer:** Prathyusha

## Check 1 – Trigger

**Result:** PASS

The Skill clearly states when it should be used, including requests such as “write the description for this PR,” “summarize this diff for review,” and “what should I put in the PR body.”

## Check 2 – Uses the actual code change

**Result:** PASS

The Skill instructs the model to inspect the real diff, branch, or changed files before writing the PR description instead of relying only on a vague user summary.

## Check 3 – Missing information

**Result:** PASS

The Skill correctly says not to invent the reason for a change when the purpose is unclear. It tells the model to ask a short question or flag the missing information.

## Check 4 – Required output format

**Result:** PASS

The Skill requires exactly four sections in this order:

* **What changed**
* **Why**
* **How to verify**
* **Least confident about**

This keeps the PR description consistent and focused on what a reviewer needs.

## Check 5 – Verification and uncertainty

**Result:** PASS

The Skill requires practical verification steps and does not allow invented tests or vague statements such as “should still work.” It also requires the author to identify areas they are least confident about.

## Check 6 – Scope

**Result:** PASS

The Skill correctly states that it only writes PR descriptions. It does not review the code, approve the PR, reject it, or decide whether it should be merged.

## Overall Result

**6/6 checks passed.**

The `write-pr-description` Skill is clear, focused, and reviewer-oriented. It uses the actual code change, avoids invented information, follows a fixed four-section structure, provides useful verification guidance, and keeps code review separate from PR-description writing.

## Suggested Improvement

Add a short self-test section with three examples that should trigger the Skill and one example that should not trigger it.
