---
name: write-tests
description: Use when the user asks to write tests, create test cases, generate unit tests, test a function or piece of code, or check code behaviour with automated tests.
---

# Write Tests

## Instructions

### 1. Understand the code

Before writing tests:

- Identify what the code is supposed to do.
- Identify its inputs and expected outputs.
- Identify important conditions, branches, and possible edge cases.
- Note any assumptions the code appears to make.

If the code's intended behaviour is unclear or important information is missing, ask for clarification rather than inventing the missing behaviour.

### 2. Decide what needs to be tested

Create tests that cover:

- Normal expected behaviour.
- Boundary or edge cases.
- Invalid or unexpected inputs.
- Important branches or conditions in the code.
- Any assumptions identified in the previous step.

Do not create unnecessary duplicate tests. Each test should check a specific behaviour or risk.

### 3. Write the tests

Use the testing framework that matches the user's programming language or project when it is clear from the context.

For each test:

- Give it a clear name that describes the behaviour being checked.
- Keep each test focused on one behaviour.
- Include the expected result.
- Use realistic but made-up test data.
- Make the test easy for another developer to understand.

If the user does not explicitly name a testing framework, stop before writing executable test code and ask which framework they want.

Do not choose a framework based only on the programming language. For example, do not automatically assume pytest for Python, JUnit for Java, or Jest for JavaScript.

Do not invent class names, object instances, import paths, file names, or project structure that the user has not provided. Ask for the missing context or clearly use a placeholder.

Do not invent functions, APIs, files, or behaviour that are not present in the code or clearly described by the user.

### 4. Format the output consistently

Always use these four headings, in this order:

#### Summary
Give a short summary of what is being tested.

#### Test Code
Provide the generated test code.

#### What Each Test Checks
Briefly explain what each individual test checks.

#### Assumptions and Missing Information
List any assumptions, missing context, or information that affected the tests.

Do not omit any of these four sections.

Do not claim that the tests pass unless they have actually been run in an environment where that can be verified.

### 5. Never do the following

- Do not invent expected behaviour that is not supported by the code or the user's description.
- Do not invent functions, APIs, files, dependencies, or test results.
- Do not ignore obvious edge cases or invalid inputs.
- Do not write tests that only repeat the same behaviour in slightly different forms.
- Do not claim that code is correct just because tests were generated.
- Do not expose secrets, API keys, passwords, or real personal data in test examples.

## Good Output Example

### User request

Write pytest tests for this Python function:

```python
def is_even(number):
    return number % 2 == 0
```

### Good response

Summary: These tests check normal even and odd numbers, zero, and negative numbers.

```python
def test_even_number():
    assert is_even(4) is True

def test_odd_number():
    assert is_even(5) is False

def test_zero():
    assert is_even(0) is True

def test_negative_even_number():
    assert is_even(-2) is True
```

What the tests check:

- `test_even_number` checks normal even-number behaviour.
- `test_odd_number` checks normal odd-number behaviour.
- `test_zero` checks an important boundary case.
- `test_negative_even_number` checks that negative values behave correctly.

Assumption: These examples assume the project uses Python with pytest.

## Bad Output Example

### Bad response

```python
def test_is_even():
    assert is_even(4) == True
```

This is bad because:

- It tests only one normal case.
- It ignores odd numbers, zero, negative numbers, and other useful cases.
- It gives no explanation of what is covered.
- It does not mention which testing framework is assumed.
- It provides no assumptions or missing-context notes.

## Self-Test Cases

### Should trigger

1. Write unit tests for this Python function.
2. Create test cases for this Java method.
3. Generate automated tests for this piece of code.

### Should not trigger

1. Explain what this Python function does.

### Awkward case

1. Write tests for this function, but the function is incomplete and its expected behaviour is not explained.