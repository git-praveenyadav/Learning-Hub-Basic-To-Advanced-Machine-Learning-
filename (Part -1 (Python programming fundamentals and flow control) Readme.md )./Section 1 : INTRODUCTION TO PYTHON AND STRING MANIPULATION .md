# Section 1: Introduction to Python & String Manipulation

**A comprehensive, beginner-friendly crash course covering Python fundamentals, dynamic typing, core data types, and powerful string manipulation toolkits tailored for data science and AI workflows.**

---

## 1. Environment Setup: Google Colab

* Google Colab is a free, cloud-based Jupyter Notebook environment that runs directly in your browser with zero local setup required.
* **Crucial Keyboard Shortcuts:**
* **Run cell & stay:** `Ctrl + Enter`
* **Run cell & move below:** `Shift + Enter`
* **Add cell below / above:** `B / A` (when not in edit mode)
* **Delete cell:** Press `D` twice (`D D`)
* **Convert cell type:** `M` (Text/Markdown) or `Y` (Code)


* **Runtime Trap:** Colab sessions disconnect after inactivity, wiping unassigned variables. Always re-run code cells from the top when reconnecting.

---

## 2. Variables & The Four Basic Data Types

* Python is dynamically typed, meaning you never need to explicitly declare data types; Python infers them automatically from the assigned value.
* **The Four Basic Types:**
* `course_name = "Data Science"` -> `str` (Text)
* `total_marks = 100` -> `int` (Whole numbers)
* `passing_score = 60.0` -> `float` (Decimals)
* `is_registered = True` -> `bool` (True / False)


* **Advanced Arithmetic Operators:**
* **Floor Division (`//`):** Divides and rounds down to the nearest integer, dropping decimals.
* **Modulo (`%`):** Returns the remainder of division.
* **Exponentiation (`**`):** Raises a number to a power.



---

## 3. String Slicing & Core Methods

* Strings are immutable sequences indexed starting from `0` or `-1` backwards.
* **Slicing Syntax:** `string[start:stop:step]`
* **1. Basic Slicing Example**
```python
text = "Data Science"
print(text[0])                          # 'D' (First character)
print(text[-1])                         # 'e' (Last character)
print(text[0:4])                        # 'Data' (Stop index 4 is EXCLUSIVE)
print(text[::2])                        # 'Dt Sene' (Every 2nd character)

```


* **2. Essential String Toolkit**
* **Whitespace Cleaning:** `messy_str.strip()` removes leading/trailing spaces, vital for CSV or API data cleaning.
* **Case Conversion:** `.lower()`, `.upper()`, and `.title()`.
* **Splitting & Joining:** `text.split(" ")` breaks strings into lists, while `" | ".join(words)` stitches them back.
* **Modern Formatting (f-strings):** `f"Student: {name} | Score: {score:.1f}%"`



---

## 4. Keypoints

* **String Multiplication vs. Length:** Multiplying a string (`'ha' * 3`) repeats the sequence into `'hahaha'`, whereas `len('ha')` counts the exact character length (`2`).
* **Index Out of Bounds:** Accessing out-of-range indices like `name[-100]` does not wrap around; it immediately throws an `IndexError`.
* **Type Mismatch in Arithmetic (`TypeError`):** Python never implicitly converts types across arithmetic operations. Trying `5 + '1'` throws a `TypeError`, so you must explicitly cast using `str()` or `int()`.
* **Assignment (`=`) vs. Comparison (`==`):** Single equals assigns values, whereas double equals checks boolean equality.
* **Floating-Point Precision Limit:** Due to binary computer storage limits, `0.1 + 0.2` outputs `0.30000000000000004` rather than clean `0.3`.
