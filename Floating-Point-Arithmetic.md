# Floating-Point Arithmetic: Issues and Limitations

Floating-point numbers in computers are represented using binary fractions (base 2), similar to how decimal numbers are represented in base 10. However, the issue arises because many decimal numbers cannot be exactly represented in binary. This leads to approximations when dealing with floating-point numbers in computers, often causing unexpected results.

## Representation of Fractions

Consider a decimal fraction like 0.625. In base 10, it is represented as:
\[ 0.625 = \frac{6}{10} + \frac{2}{100} + \frac{5}{1000} \]

In base 2 (binary), the number 0.625 is represented as:
\[ 0.625 = \frac{1}{2} + \frac{0}{4} + \frac{1}{8} \]
This is straightforward because it can be expressed precisely using powers of 2.

However, many decimal fractions cannot be exactly represented in binary. For example, 1/10 in decimal is:
\[ 0.1 \text{ (in base 10)} \]

In binary, this fraction is an infinitely repeating sequence:
\[ 0.1 = 0.00011001100110011001100110011\ldots \text{ (repeating)} \]

If we truncate this repeating sequence, we get an approximation. In most computers, binary floating-point numbers are approximated using 53 bits for precision (in double-precision format).

For instance, 0.1 in binary is approximated as:
\[ \frac{3602879701896397}{2^{55}} \]
This is a close approximation, but not exactly equal to 1/10. On most systems, this binary approximation is used to store 0.1.


## Floating-Point Approximation and Display

Even though the value stored for 0.1 is an approximation, Python (and many other programming languages) only displays a rounded version of this value. If Python were to display the exact internal binary representation of 0.1, it would be:
```
0.1000000000000000055511151231257827021181583404541015625
```
However, Python rounds this to the simpler:
```
0.1
```
This rounded representation gives the illusion of exactness, but the actual stored value is an approximation. Interestingly, many different decimal numbers (like 0.1, 0.10000000000000001, and others) share the same closest binary approximation.

## Examples of Floating-Point Errors

Floating-point arithmetic can lead to errors that are not immediately obvious. For instance, summing three values of 0.1:
```python
0.1 + 0.1 + 0.1 == 0.3
```
This results in:
```
False
```
This happens because 0.1 cannot be exactly represented, and summing multiple approximations introduces small errors. Even rounding the values using Python's `round()` function does not eliminate the error:
```python
round(0.1, 1) + round(0.1, 1) + round(0.1, 1) == round(0.3, 1)
```
This also results in:
```
False
```
However, the `math.isclose()` function can help compare inexact floating-point values within a tolerance:
```python
import math
math.isclose(0.1 + 0.1 + 0.1, 0.3)
```
This results in:
```
True
```

## Handling Floating-Point Precision

To mitigate the effects of floating-point errors, Python provides several methods:

- **String Formatting**: You can format floating-point numbers to display only a certain number of significant digits, avoiding confusion with excessive precision:
  ```python
  format(math.pi, '.12g')  # 12 significant digits
  format(math.pi, '.2f')   # 2 digits after the decimal point
  ```

- **`sum()` with Extended Precision**: The built-in `sum()` function uses extended precision for intermediate rounding steps, reducing errors when summing many values:
  ```python
  sum([0.1] * 10) == 1.0
  ```

- **`math.fsum()`**: This function is even more accurate, as it tracks all the intermediate digits to minimize rounding errors:
  ```python
  math.fsum(arr)
  ```

## When Exact Arithmetic is Needed

For applications that require exact decimal arithmetic (e.g., financial calculations), Python provides the **`decimal`** and **`fractions`** modules:
- **`decimal` module**: This implements decimal arithmetic and is useful for high-precision operations.
- **`fractions` module**: This works with rational numbers, so fractions like 1/3 can be represented exactly.

## Analyzing the `0.1` Example in Detail

The primary issue with floating-point representation is that certain decimal fractions (like 0.1) cannot be represented exactly in binary. In IEEE 754 double-precision format (binary64), 0.1 is represented as:
\[ \frac{7205759403792794}{2^{56}} \]
This is a good approximation of 1/10, but it is slightly larger. The value stored in memory for 0.1 is:
```
0.1000000000000000055511151231257827021181583404541015625
```
To analyze this more precisely, you can use the `as_integer_ratio()` method:
```python
(0.1).as_integer_ratio()
```
This returns:
```
(3602879701896397, 36028797018963968)
```
This exact ratio can be used to represent 0.1 precisely in rational form.
