# Section 7: Numerical Computing with NumPy

**A comprehensive guide covering NumPy array creation, vectorization, attributes, slicing, boolean masking, reshaping, aggregations, and high-yield exam traps.**

---

## 1. Syntax & Construction (NumPy Arrays & Creation)

* **Importing NumPy:** Standard convention is `import numpy as np`.
* **Array Creation (`np.array()`):** Converts Python lists (1D or nested lists for 2D/ND) into uniform, high-speed NumPy `ndarray` structures.
* **Built-in Array Creation Functions:**
* `np.zeros(n)`: Generates an array of $n$ zeros (`float` type by default).
* `np.ones(n)`: Generates an array of $n$ ones.
* `np.arange(start, stop)`: Generates integers from `start` up to `stop` (exclusive upper bound).
* `np.linspace(start, stop, n)`: Generates $n$ evenly spaced values between `start` and `stop`.
* `np.random.randint(low, high, size)`: Generates random integers within a specified range and shape.
* `np.random.seed(value)`: Sets a fixed random seed to ensure reproducibility across runs.



---

## 2. Core Coding Concepts & Syntax Patterns

* **1. Vectorization vs. Python Loops**
* Vectorization applies mathematical operations to entire arrays simultaneously without explicit `for` loops, pushing heavy lifting down to optimized C code.


* **2. Array Attributes (`ndim`, `shape`, `size`, `dtype`)**
* `arr.ndim`: Returns the number of dimensions (e.g., `1` for 1D, `2` for 2D).
* `arr.shape`: Returns a tuple representing row and column counts `(rows, cols)`.
* `arr.size`: Returns the total element count across all dimensions (product of shape dimensions).
* `arr.dtype`: Returns the data type of the stored elements (e.g., `'int64'`, `'float64'`).


* **3. Indexing and Slicing (1D and 2D)**
* **1D Slicing:** `arr[start:stop:step]` (stop index is exclusive).
* **2D Slicing:** `score_table[row_selector, col_selector]` (comma separates dimensions).
* `score_table[:, 1]` extracts all rows for column index `1`.




* **4. Boolean Masking and Conditional Replacement (`np.where()`)**
* **Boolean Mask:** `mask = arr > 50` produces an array of `True`/`False` values.
* **Filtering:** `arr[mask]` extracts only elements where the condition is `True`.
* `np.where(condition, x, y)`: Wherever `condition` is `True`, places `x`; otherwise places `y`.


* **5. Reshaping and Flattening**
* `arr.reshape(rows, cols)`: Rearranges array dimensions without altering data, provided total element count remains identical. Use `-1` for automatic dimension inference.
* `arr.flatten()`: Converts multi-dimensional arrays into a 1D vector.



---

## 3. Operations, Methods & Built-In Functions Reference

* **Vectorized Arithmetic:** Operators like `+`, `-`, `*`, `/`, `**` act element-wise across arrays.
* **Aggregation Functions:** `np.sum()`, `np.mean()`, `np.min()`, `np.max()`, `np.median()`.
* **Axis Parameter Control in Aggregations:**
* `axis=0`: Aggregates across rows, collapsing the row dimension to yield one value per column.
* `axis=1`: Aggregates across columns, collapsing the column dimension to yield one value per row.



---

## 4. Keypoints

* **Reshape Element Count Mismatch (`ValueError`):** The product of the target shape dimensions in `.reshape()` must precisely match the array's total `.size`. For example, reshaping a 12-element array to `(5, 3)` raises a `ValueError` because $5 \times 3 = 15 \neq 12$.
* **Confusing `len()` with `.shape` or `.size` on 2D Arrays:** Calling `len(arr)` on a 2D array returns only the row count (length of the first axis), whereas `.size` returns the total element count across all rows and columns.
* **Omitting the Axis Parameter in Multi-Dimensional Aggregations:** Calling `np.mean(score_table)` without specifying an `axis` computes a single grand mean across every element in the entire 2D table, rather than per-row or per-column summaries.
* **Mixed-Type Implicit Upcasting:** Passing a Python list with mixed types (e.g., integers and strings) into `np.array()` forces NumPy to silently convert everything to a uniform string data type.
* **Misinterpreting `np.arange()` Upper Bounds:** `np.arange(1, 10)` stops at `9` (exclusive upper bound), producing elements `1` through `9`. To include `10`, the stop parameter must be `11` (`np.arange(1, 11)`).
* **Matrix Multiplication vs. Element-wise Multiplication:** The standard `*` operator on NumPy arrays performs element-wise multiplication (corresponding pairs multiplied together), not linear algebra matrix/dot products (`@` or `np.dot()`).
