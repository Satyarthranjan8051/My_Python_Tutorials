# Secant Method Root Finding Algorithm in Python

This repository demonstrates the implementation of the **Secant Method**, an efficient numerical technique for root finding. This method is similar to the Newton-Raphson method but avoids the need to compute derivatives.

## 👨‍💻 Author: Satyarth Ranjan  
**UID**: 21BCS8388  

---

## 📜 Table of Contents

1. [Introduction](#introduction)
2. [Secant Method](#secant-method)
    - [Theory](#secant-theory)
    - [Code Explanation](#secant-code)
3. [How to Run](#how-to-run)
4. [Conclusion](#conclusion)

---

## 🧠 Introduction

In this project, we implement the **Secant Method** for finding the roots of a given function. The method is iterative, similar to the Newton-Raphson method, but it approximates the derivative by using two prior function evaluations.

---

## 🔍 Secant Method

### <a id="secant-theory">Theory</a>

The **Secant Method** is a numerical technique used to find the roots of a given function without requiring its derivative. It uses two initial approximations `x0` and `x1`, and iteratively finds the intersection of the secant line through these points with the x-axis. The formula for the next approximation is:

\[
x_{\text{new}} = x_1 - f(x_1) \cdot \frac{x_1 - x_0}{f(x_1) - f(x_0)}
\]

This method is based on a simple idea: instead of using the derivative (as in the Newton-Raphson method), the Secant Method approximates the derivative by using the slope between two points. The main advantage is that it doesn't require explicit calculation of the derivative, which can be a significant benefit for complex functions.

#### Convergence:

The Secant Method typically converges faster than the **Bisection Method** but slower than the **Newton-Raphson Method**. However, when the derivative is difficult or expensive to compute, the Secant Method is often preferred. It converges **superlinearly**, meaning it converges faster than linear methods like bisection but may require more iterations than quadratic methods like Newton-Raphson.

#### Advantages:
- Does not require the computation of the derivative of the function.
- Faster convergence than the Bisection Method.
- Suitable for continuous functions where the derivative may not be easily accessible.

#### Disadvantages:
- May fail if the function is not well-behaved in the region of the root (e.g., discontinuities).
- Convergence is not guaranteed for poorly chosen initial guesses.

### <a id="secant-code">Code Explanation</a>

```python
def secant_method(f, x0, x1, tol=1e-5, max_iter=100):
    for i in range(max_iter):
        f_x0 = f(x0)
        f_x1 = f(x1)
        x_new = x1 - f_x1 * (x1 - x0) / (f_x1 - f_x0)
        if abs(x_new - x1) < tol:
            return x_new

        # Update the guesses
        x0, x1 = x1, x_new

    raise ValueError(f"Root not found within {max_iter} iterations.")
```


- **Input**: The function `f`, initial guesses x0 and x1, tolerance `tol`, and max iterations `max_iter`.
- **Logic**: It computes the new approximation based on the secant line formula and checks if the tolerance condition is satisfied.
- **Output**: The approximate root of the function.

#### Example:

```python
if __name__ == "__main__":
    def f(x):
        return x**2 - 2
    x0 = 0
    x1 = 2
    root = secant_method(f, x0, x1)
    print("Root is approximately:", root)
```

Output:
```csharp
Root is approximately: 1.4142135626888697
```
---

## 🏃‍♂️ How to Run

1. Clone this repository:
    ```bash
    git clone https://github.com/Satyarthranjan8051/Numeric-Method-and-Optimization-Using-Python.git
    ```

2. Navigate to the project directory:
    ```bash
    cd Assignment 1.4
    ```

3. Run the Python script:
    ```bash
    Root finding method(Secant).ipynb
    ```

---

## ⚡ Conclusion

In this project, we implemented the Secant Method for root finding in Python. The method efficiently finds roots of non-linear equations without needing the derivative, making it a good alternative to Newton-Raphson in certain scenarios.

Feel free to experiment with different functions to explore the behavior of the Secant Method in root finding!
