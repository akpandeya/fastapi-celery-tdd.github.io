---

layout: page
title: Test-Driven Development (TDD) Refresher
nav_order: 1
parent: Chapter 1 - Project Setup and Hello World API

---

## What is Test-Driven Development (TDD)?

Test-Driven Development (TDD) is a software development approach where you write automated tests before writing the code. The idea behind TDD is to focus on the desired behavior of the code, and ensure that the code works as expected.

The TDD process typically involves three steps:

1. *writing a failing test*,
2. writing just enough code to *make the test pass*, and
3. then *refactoring the code* to improve its design and maintainability.

## Why use TDD?

TDD is important for the same reason that getting feedback on your code is important. Just like code reviews and stakeholder reviews, TDD provides feedback about your code. However, writing tests first gives you feedback even before you've written your code. It helps you ensure that your code is correct and easy to use. Of course, you can still test the correctness of code even after you've written it.

Writing tests before writing the code may seem strange and difficult at first, but it becomes easier with practice. It's worth it because it can catch bugs earlier in the development process, when they're cheaper and easier to fix. It also helps ensure that changes to the code don't introduce new bugs and that the code works as expected.

TDD can also help you create better code that is easier to maintain. By writing tests before writing the code, you are forced to think about how the code should work, what inputs it should take, and what outputs it should produce. This can lead to better overall design and more maintainable code.

## TDD Example: Implementing a function to calculate the sum of numbers
Let's walk through an example to see how TDD can be used to implement a function that calculates the sum of numbers. This is a simple example, but it's still helpful for understanding the TDD process.

### Step 1: Write a failing test for adding two numbers

Our first step is to write a test that specifies the behavior we want our function to have. Here's an example:

```python
def test_sum_two_numbers():
    assert sum_numbers(2, 3) == 5
    assert sum_numbers(2.1, 3.5) == 5.6
```

This test checks that our function `sum_numbers` can correctly calculate the sum of two input numbers, both integers and floating point numbers.

### Step 2: Write just enough code to make the test pass

Now that we have a failing test, we need to write just enough code to make it pass. Here's an implementation of the `sum_numbers` function that makes the test pass:

```python
def sum_numbers(a, b):
    return a + b
```

In this implementation, we are adding two numbers and returning the result.

### Step 3: Refactor the code

Although there isn't much code to refactor in this case, it's important to add type hints to ensure maintainability. We may also want to give more descriptive parameter names that convey our intent. Here's a revised version of `sum_numbers`:

```python
from typing import Union

def sum_numbers(
    num1: Union[int, float], 
    num2: Union[int, float]
) -> Union[int, float]:
    return num1 + num2
```

We could add more test cases to check for different types of corner cases. It's important to consider such cases, as they are where our code is most likely to fail. For example, what happens when we add 0?

We could write more tests, but we'd be repeating ourselves. Instead, we can use `pytest` to parametrize the tests, so the same test runs multiple times with different input and output values:

```python
import pytest

@pytest.mark.parametrize(
    ["num1", "num2", "expected_result"],
    [
        (2, 3, 5),
        (2.1, 3.5, 5.6),
        (2, 0, 2),
        (0, 3, 3),
    ]
)
def test_sum_numbers(num1, num2, expected_result):
    assert sum_numbers(num1, num2) == expected_result
```

This code looks much cleaner and more concise than before.

### Step 4: Write additional failing tests for adding more numbers

Now that we have a passing test for adding two numbers, let's write additional failing tests to check that our function works correctly for adding more than two numbers. Here are a few examples:

```python
@pytest.mark.parametrize(
    ["num1", "num2", "num3", "expected_result"],
    [
        (2, 3, 5, 10),
        (0, 3.1, 4.5, 7.6),
        (-2.5, 2.5, 4.1, 4.1),
        (3, 0, 0, 3),
    ]
)
def test_sum_three_numbers(num1, num2, num3, expected_result):
    assert sum_numbers(num1, num2, num3) == expected_result
```

These tests check that our function can correctly calculate the sum of any number of input numbers.

### Step 5: Write more code to fix the tests

Now that the tests will fail again, it's time to re-implement the function:

```python
from typing import Union

def sum_numbers(
    num1: Union[int, float], 
    num2: Union[int, float],
    num3: Union[int, float],

) -> Union[int, float]:
    return num1 + num2 + num3
```

This implementation makes our newly written test pass, but our old test will fail. To fix this, we could provide a default value for `num3`:

```python
from typing import Union

def sum_numbers(
    num1: Union[int, float], 
    num2: Union[int, float],
    num3: Union[int, float] = 0

) -> Union[int, float]:
    return num1 + num2 + num3
```

### Step 6: Refactor the code to improve its design and maintainability

All the tests should be passing now, so it's time to refactor our code to make it more maintainable. Here's one possible refactor:

```python
from typing import Union

def sum_numbers(
    *numbers: Union[int, float]

) -> Union[int, float]:
    result = 0

    for number in numbers:
        result += number

    return result
```

This implementation accepts any number of input numbers using the `*args` syntax, calculates their sum using a loop, and returns the result. This implementation is more flexible and easier to read than the previous implementation.

We could add more test cases and further refactor our implementation until we're happy with it.

## Conclusion

In this post, we have learned about Test-Driven Development (TDD) and its benefits. We saw how TDD can help us write better code, catch bugs earlier, and make our code more maintainable by providing early feedback.

If you're interested in learning more about TDD, there are many online resources available, including tutorials on YouTube.

Here are some additional tips for using TDD:

**Start small:** When starting out with TDD, it's best to begin with small, simple functions. This will help you get comfortable with the process and prevent you from feeling overwhelmed.

**Keep your tests focused:** Each test should focus on testing one specific behavior of your code. This makes it easier to debug your tests and identify any problems.

**Refactor your code often:** As you add new features to your code, it's important to refactor your code regularly. This keeps your code clean and maintainable.

**Don't be afraid to break your tests:** Sometimes, you may need to break your tests to add new features to your code. This is okay! Just make sure you fix the tests as soon as possible.

TDD can be an effective way to improve the quality of your code. By following these tips, you can get started with TDD and start writing better code today! Thank you for reading!
