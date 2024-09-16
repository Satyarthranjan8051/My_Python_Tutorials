
# Root Finding Algorithms in Python

This repository demonstrates the implementation of two important numerical methods for root finding: **Bisection Method** and **Newton-Raphson Method**. These algorithms are widely used for solving equations where an explicit algebraic solution is not possible.

## 👨‍💻 Author: Satyarth Ranjan  
**UID**: 21BCS8388  

---

## 📜 Table of Contents

1. [Introduction](#introduction)
2. [Bisection Method](#bisection-method)
    - [Theory](#bisection-theory)
    - [Code Explanation](#bisection-code)
3. [Newton-Raphson Method](#newton-raphson-method)
    - [Theory](#newton-theory)
    - [Code Explanation](#newton-code)
4. [How to Run](#how-to-run)
5. [Conclusion](#conclusion)

---

## 🧠 Introduction

In this project, we implement two widely used root-finding algorithms in Python. These methods allow us to find the solution to non-linear equations where analytical methods might be inefficient or infeasible.

- **Bisection Method** is a simple iterative method based on the Intermediate Value Theorem.
- **Newton-Raphson Method** is a more sophisticated approach utilizing derivatives to approximate the root faster.

---

## 🔍 Bisection Method

### <a id="bisection-theory">Theory</a>

The **Bisection Method** is based on the Intermediate Value Theorem, which states that for any continuous function `f(x)` in an interval `[a, b]` where `f(a)` and `f(b)` have opposite signs, there exists at least one root between `a` and `b`.

This method repeatedly bisects the interval and selects the subinterval where the sign of the function changes, narrowing down the possible location of the root. This process is continued until the root is found within a predefined tolerance.

### <a id="bisection-code">Code Explanation</a>

```python
def bisection_method(func, a, b, tol=1e-6, max_iter=100):
    if func(a) * func(b) > 0:
        raise ValueError("The function values at the interval endpoints must have opposite signs.")

    iteration = 0

    while (b - a) / 2 > tol and iteration < max_iter:
        c = (a + b) / 2
        if func(c) == 0:
            return c  # Found exact root
        elif func(c) * func(a) < 0:
            b = c
        else:
            a = c
        iteration += 1

    return (a + b) / 2
```

- **Input**: The function `func`, interval `[a, b]`, tolerance `tol`, and max iterations `max_iter`.
- **Logic**: The midpoint `c` is calculated and checked if it is a root. If not, the interval is adjusted, and the process is repeated.
- **Output**: The approximate root of the function in the interval.

#### Example:

```python
def quadratic_function(x):
    return x**2 - 4

root = bisection_method(quadratic_function, 0, 3)
print("Bisection Method Root:", root)
```

Output:
```
Bisection Method Root: 2.000000238418579
```

---

## 🔍 Newton-Raphson Method

### <a id="newton-theory">Theory</a>

The **Newton-Raphson Method** uses the idea of linear approximation. Given a function `f(x)` and its derivative `f'(x)`, the next approximation to the root is given by:

\[ x_{n+1} = x_n - rac{f(x_n)}{f'(x_n)} \]

This method converges much faster than the bisection method but requires the derivative of the function.

### <a id="newton-code">Code Explanation</a>

```python
def newton_raphson_method(func, func_derivative, initial_guess, tol=1e-6, max_iter=100):
    x = initial_guess
    iteration = 0

    while abs(func(x)) > tol and iteration < max_iter:
        x = x - func(x) / func_derivative(x)
        iteration += 1

    return x
```

- **Input**: The function `func`, its derivative `func_derivative`, initial guess `initial_guess`, tolerance `tol`, and max iterations `max_iter`.
- **Logic**: The formula \( x_{n+1} = x_n - rac{f(x_n)}{f'(x_n)} \) is used iteratively until the root is found or the iteration limit is reached.
- **Output**: The approximate root of the function.

#### Example:

```python
def cubic_function(x):
    return x*3 - 6*x*2 + 11*x - 6

def cubic_derivative(x):
    return 3*x**2 - 12*x + 11

initial_guess = 1.5
root_newton = newton_raphson_method(cubic_function, cubic_derivative, initial_guess)
print("Newton-Raphson Method Root:", root_newton)
```

Output:
```
Newton-Raphson Method Root: -0.7650845376740406
```

---

## 🏃‍♂️ How to Run

1. Clone this repository:
    ```bash
    git clone <repo-link>
    ```

2. Navigate to the project directory:
    ```bash
    cd <directory>
    ```

3. Run the Python script:
    ```bash
    python root_finding.py
    ```

---

## ⚡ Conclusion

In this project, we have successfully implemented two different root-finding algorithms, Bisection Method and Newton-Raphson Method, in Python. Both methods have their advantages, with the Bisection Method being simple and reliable, while the Newton-Raphson Method converges faster with the use of derivatives.

Feel free to play around with different functions to understand the working of these methods better!
