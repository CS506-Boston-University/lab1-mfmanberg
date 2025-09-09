[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/1wPaDLtk)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=20411978&assignment_repo_type=AssignmentRepo)
# Polynomial Expression System - Student Exercise

This project implements a symbolic polynomial expression system in Python that allows you to build and represent polynomial expressions using a tree-like structure. **This is a student exercise where you'll implement missing functionality.**

## Current State

The code provides the following classes with **incomplete implementations**:

### Core Classes (Partially Implemented)

- **`X`**: Represents the variable X in polynomial expressions ✅ **Complete**
- **`Int`**: Represents integer constants in polynomial expressions ✅ **Complete**
- **`Add`**: Represents addition of two polynomial expressions ✅ **Complete**
- **`Mul`**: Represents multiplication of two polynomial expressions ✅ **Complete**
- **`Sub`**: Represents subtraction of two polynomial expressions ❌ **Needs Implementation**
- **`Div`**: Represents division of two polynomial expressions ❌ **Needs Implementation**

### Methods (Partially Implemented)

- **`__repr__`**: String representation ✅ **Complete for X, Int, Add, Mul**
- **`evaluate(x_value)`**: Computes polynomial value for given X ❌ **Needs Implementation**
- **`simplify()`**: Simplifies expressions ❌ **Optional Exercise**

## Exercise Overview

You have **3 exercises** to complete:

1. **Exercise 1**: Implement `Sub` and `Div` classes
2. **Exercise 2**: Implement `evaluate` methods for all classes
3. **Exercise 3**: Implement `simplify` methods (Optional)

---

## Exercise 1: Implement Sub and Div Classes

### Objective
Complete the `Sub` and `Div` classes to handle polynomial subtraction and division.

### What You Need to Implement

#### Sub Class
```python
class Sub:
    def __init__(self, p1, p2):
        self.p1 = p1
        self.p2 = p2
    
    def __repr__(self):
        # TODO: Implement string representation for subtraction
        # Should handle parentheses similar to Mul class
        # Hint: Look at how Mul class handles parentheses
        pass
```

#### Div Class
```python
class Div:
    def __init__(self, p1, p2):
        self.p1 = p1
        self.p2 = p2
    
    def __repr__(self):
        # TODO: Implement string representation for division
        # Should handle parentheses similar to Mul class
        # Hint: Look at how Mul class handles parentheses
        pass
```

### Requirements
- **String Representation**: Handle parentheses correctly for mathematical notation
- **Precedence Rules**: Follow the same pattern as `Mul` class
- **Examples**:
  - `Sub(Int(10), Int(3))` should print as `10 - 3`
  - `Sub(Add(Int(2), Int(3)), Int(4))` should print as `( 2 + 3 ) - 4`
  - `Div(Int(15), Int(3))` should print as `15 / 3`
  - `Div(Sub(Int(10), Int(2)), Int(4))` should print as `( 10 - 2 ) / 4`

### Hints
- Look at how the `Mul` class handles parentheses in its `__repr__` method
- Use `isinstance()` to check if operands need parentheses
- Subtraction and division have the same precedence as addition and subtraction respectively

---

## Exercise 2: Implement Evaluate Methods

### Objective
Add `evaluate(x_value)` methods to all classes to compute polynomial values.

### What You Need to Implement

#### For Each Class
```python
def evaluate(self, x_value):
    # TODO: Implement evaluation logic
    pass
```

### Requirements by Class

#### X Class
- Should return `Int(x_value)` - the value of X

#### Int Class  
- Should return `Int(self.i)` - the stored integer value

#### Add Class
- Should evaluate both operands and return their sum
- Example: `Add(Int(3), Int(5)).evaluate(0)` should return `Int(8)`

#### Mul Class
- Should evaluate both operands and return their product
- Example: `Mul(Int(3), Int(5)).evaluate(0)` should return `Int(15)`

#### Sub Class
- Should evaluate both operands and return their difference
- Example: `Sub(Int(10), Int(3)).evaluate(0)` should return `Int(7)`

#### Div Class
- Should evaluate both operands and return their quotient (use integer division `//`)
- Example: `Div(Int(15), Int(3)).evaluate(0)` should return `Int(5)`

### Test Examples
```python
# Simple evaluation
poly = Add(Mul(Int(2), X()), Int(3))  # 2*X + 3
result = poly.evaluate(5)  # Should return Int(13)

# Complex evaluation
complex_poly = Add(Sub(Mul(Int(2), X()), Int(1)), Div(Int(6), Int(2)))
result = complex_poly.evaluate(4)  # Should return Int(10)
```

---

## Exercise 3: Implement Simplify Methods (Optional)

### Objective
Add `simplify()` methods to all classes to simplify polynomial expressions.

### What You Need to Implement

#### For Each Class
```python
def simplify(self):
    # TODO: Implement simplification logic
    pass
```

### Simplification Rules

#### X and Int Classes
- Cannot be simplified further, return `self`

#### Add Class
- `X + 0` → `X`
- `0 + X` → `X`
- `3 + 5` → `8`
- `X + X + X` → `3 * X` (advanced)

#### Mul Class
- `X * 0` → `0`
- `X * 1` → `X`
- `3 * 5` → `15`

#### Sub Class
- `X - 0` → `X`
- `5 - 3` → `2`

#### Div Class
- `X / 1` → `X`
- `6 / 2` → `3`

### Advanced Simplification (Bonus)
- Combine like terms: `X + X + X` → `3 * X`
- Factor expressions: `2 * X + 4 * X` → `6 * X`

### Example
```python
# Before simplification
expr = Add(Add(X(), Int(0)), Mul(Int(2), Int(3)))
print(expr)  # X + 0 + 2 * 3

# After simplification
simplified = expr.simplify()
print(simplified)  # X + 6
```

---

## Running the Code

### Basic Demo
```bash
python polynomial.py
```

### Run Tests
```bash
# Run comprehensive test suite
python test_polynomial.py

# Or run through main file
python polynomial.py --test
```

The test suite will show you which exercises you've completed and which still need work.

---

## File Structure

```
polynomial/
├── polynomial.py           # Main implementation file (your work goes here)
├── test_polynomial.py      # Comprehensive test suite
├── README.md              # This file
├── .gitignore             # Python gitignore file
└── .github/
    └── workflows/
        └── test.yml       # GitHub Actions workflow
```

## GitHub Actions

This repository includes a GitHub Actions workflow that automatically runs tests when you push code or create pull requests. The workflow:

- **Tests on multiple Python versions** (3.8, 3.9, 3.10, 3.11, 3.12)
- **Runs all test suites** to verify your implementations
- **Analyzes exercise progress** and shows which parts are completed
- **Checks code quality** with linting tools (flake8, black, isort)
- **Validates syntax** to catch basic errors

### Workflow Features

- ✅ **Multi-version testing**: Ensures your code works across Python versions
- ✅ **Progress tracking**: Shows which exercises you've completed
- ✅ **Code quality checks**: Helps maintain clean, readable code
- ✅ **Automatic triggers**: Runs on push, pull requests, and manual triggers
- ✅ **Detailed feedback**: Clear status indicators for each exercise

### Viewing Results

1. Go to the **Actions** tab in your GitHub repository
2. Click on the latest workflow run
3. View detailed results for each Python version
4. Check the "exercise-progress" job for completion status

---

## Getting Started

1. **Start with Exercise 1**: Implement the `Sub` and `Div` classes
2. **Run tests**: Use `python test_polynomial.py` to see your progress
3. **Move to Exercise 2**: Implement the `evaluate` methods
4. **Test again**: Verify all evaluation tests pass
5. **Try Exercise 3**: Implement simplification (optional)

## Tips

- **Read the existing code**: Look at how `Add` and `Mul` classes work
- **Use the tests**: They'll guide you on what to implement
- **Start simple**: Get basic functionality working first
- **Test frequently**: Run tests after each small change
- **Ask questions**: The TODO comments provide hints

Good luck! 🚀