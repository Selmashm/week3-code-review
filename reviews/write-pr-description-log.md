# Review Log – `write-pr-description`

**Skill reviewed:** `skills/write-pr-description/SKILL.md`
**Reviewer:** Prathyusha

## Test 1 – Correct trigger

**Input:** “Write the description for this PR.”

**Result:** PASS

The Skill correctly triggered for a PR-description request and produced a reviewer-focused description.

## Test 2 – Uses the actual change

**Input:** A code diff was provided with a request to summarize it for review.

**Result:** PASS

The Skill focused on the actual code change instead of relying only on a vague summary.

## Test 3 – Missing reason

**Input:** A code change was provided without explaining why it was made.

**Result:** PASS

The Skill did not invent a business reason. It used only information supported by the change and identified the missing context.

## Test 4 – Output structure

**Input:** Asked to generate a PR description for a normal code change.

**Result:** PASS

The Skill used the required four sections:

* What changed
* Why
* How to verify
* Least confident about

It did not add unnecessary extra sections.

## Test 5 – Non-PR request

**Input:** “Review this code and find bugs.”

**Result:** PASS

The Skill did not treat the request as a PR-description task, because code review belongs to the `review-pr` Skill.

## Overall Result

**5/5 tests passed.**

The Skill consistently created concise PR descriptions, stayed focused on the actual code change, avoided inventing missing information, followed the required four-section structure, and kept PR-description writing separate from code review.

## Suggested Improvement

Add a short self-test section with three prompts that should trigger the Skill and one prompt that should not trigger it.
