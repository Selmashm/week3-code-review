---
name: review-pr
description: Use when the user asks for a code review, asks to review a pull request or code change, or asks to find issues in code changes.
---

# Review a Pull Request

## Purpose

Review a code change systematically and report useful, evidence-based findings.

The review must identify problems without making assumptions that are not supported by the provided code or context.

Do not approve or reject the pull request. The review reports findings; a human makes the final decision.

## Review Process

### 1. Understand the change

Identify what the code change is intended to do based on the pull request description and the code provided.

If the purpose of the change is unclear or missing, state that the intended behaviour cannot be confirmed and do not make assumptions.

### 2. Check correctness

Compare the intended behaviour with the actual code.

Check for:

- Logic that does not match the stated purpose.
- Missing functionality.
- Incorrect implementation.
- Behaviour that could produce an incorrect result.

Only report problems that are supported by the provided code or context.

### 3. Check bad or unexpected input

Check how the code handles invalid, missing, unexpected, or relevant boundary inputs.

Identify cases where the code could:

- Fail unexpectedly.
- Produce an incorrect result.
- Behave unsafely.

Do not invent unrealistic edge cases or report an issue when the available context does not support it.

### 4. Check security

Check the code change for:

- API keys.
- Passwords.
- Access tokens.
- Credentials.
- Other exposed secrets or sensitive information.

Flag credentials or secrets that appear to be hard-coded or exposed in the change.

Only report a security issue when there is evidence in the provided code or context.

### 5. Check clarity

Check whether the changed code is clear enough for another developer to understand and maintain.

Look for:

- Unclear naming.
- Confusing logic.
- Undocumented assumptions.
- Other ambiguity that could reasonably confuse a future reader.

Do not report subjective style preferences unless they affect understanding, maintainability, or correctness.

### 6. Check for other important issues

Identify other significant problems introduced by the change that were not covered by the checks above.

Only report issues supported by the provided code or context.

## Severity

Classify every finding as one of the following:

### Must fix

Use this when the problem should be fixed before the change is merged because it could cause a significant problem.

Examples include:

- Incorrect core functionality.
- Serious errors with normal input.
- Exposed credentials or serious security problems.
- Important missing functionality.

### Should fix

Use this when the problem should be fixed but is not severe enough to block the change by itself.

Examples include:

- Less serious edge cases.
- Significant clarity or maintainability issues.
- Smaller reliability problems.

### Optional

Use this for improvements that would make the code better but are not significant defects.

Examples include:

- Minor readability improvements.
- Clearer naming.
- Small refactoring suggestions.

Do not present optional improvements as defects.

## Reporting Findings

For every finding:

1. State the problem clearly.
2. Provide evidence from the code or context.
3. Explain why it matters.
4. Suggest what could be changed when appropriate.
5. Assign one severity: Must fix, Should fix, or Optional.

If there is not enough information to confirm an issue, state what information is missing instead of guessing.

## Output Format

Use this structure:

### Summary

Give a short overview of the main findings.

### Must fix

List serious findings.

If there are none, write "None found."

### Should fix

List important but non-blocking findings.

If there are none, write "None found."

### Optional

List smaller improvements.

If there are none, write "None found."

### Questions / Missing Information

List anything that could not be confirmed because information was missing.

If there are none, write "None."

End with:

**Human approval is required. This review reports findings but does not approve or reject the pull request.**

## Good Output Example

### Summary

The change correctly calculates the total for normal positive quantities, but it does not handle negative quantities.

### Must fix

None found.

### Should fix

**Negative quantity is not handled**

**Evidence:** `calculate_total()` multiplies the price by the quantity without checking whether the quantity is negative.

**Why it matters:** A negative quantity could produce an invalid order total.

**Suggested change:** Validate that the quantity is within the range allowed by the application before calculating the total.

### Optional

None found.

### Questions / Missing Information

It is unclear whether a quantity of zero is valid for this application.

**Human approval is required. This review reports findings but does not approve or reject the pull request.**

## Bad Output Example

This code looks good overall.

Maybe improve the variable names and add more error handling.

I think the PR can be approved.

This is a bad review because it does not provide specific findings or evidence, does not use the required severity categories, does not explain what was checked, and incorrectly approves the pull request.
