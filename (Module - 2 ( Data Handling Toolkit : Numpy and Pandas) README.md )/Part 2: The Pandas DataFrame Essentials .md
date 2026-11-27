# Part 2 : The Pandas DataFrame Essentials

**A comprehensive guide covering DataFrame construction, CSV I/O, indexing with `.loc`, data inspection, boolean filtering, missing values, and high-yield exam traps.**

---

## 1. Syntax & Construction (Pandas DataFrames & I/O)

* **Importing Pandas & NumPy:** Standard aliases are `import pandas as pd` and `import numpy as np`.
* **DataFrame Construction from Dictionary of Lists:** `df = pd.DataFrame({"Name": ["A", "B"], "Age": [21, 22]})`
* Each dictionary key becomes a column label; each list becomes the column's values.
* Pandas automatically assigns default integer row indices (`0, 1, 2, ...`).


* **Writing & Reading CSV Files (Round-Trip):**
* Save to CSV: `df.to_csv("file.csv", index=False)` (prevents writing row indices as an extra column).
* Load from CSV: `df = pd.read_csv("file.csv")` (loads CSV from disk/path into a DataFrame).



---

## 2. Core Coding Concepts & Syntax Patterns

* **1. DataFrame vs. Series vs. NumPy Array**
* **DataFrame:** 2D labeled tabular structure (rows + columns) built on top of NumPy arrays; each column is stored as an underlying NumPy array / Series and can have its own `dtype`.
* **Series:** 1D labeled column extracted from a DataFrame (`df["ColName"]`).
* **NumPy vs. Pandas:** Not alternatives—NumPy is the numerical foundation; Pandas wraps it with human-readable column labels and mixed-column tabular support.


* **2. Column Selection & Row Selection (`.loc`)**
* **Single Column (returns Series):** `df["Name"]`
* **Multiple Columns (returns DataFrame):** `df[["Name", "Marks"]]` (list inside brackets)
* **Column Names List:** `df.columns.tolist()`
* **Row Selection by Label:**
* Single row: `df.loc[0]`
* Slice range: `df.loc[0:2]` (inclusive on BOTH start and stop labels, unlike standard Python slicing)


* **Dimensions:** `df.shape` returns `(num_rows, num_columns)`.


* **3. Initial Data Inspection (`.head()`, `.tail()`, `.info()`, `.describe()`)**
* `df.head(n)` / `df.tail(n)`: Displays first/last `n` rows (default `n=5`).
* `df.info()`: Structural/metadata summary—index range, column count, per-column non-null count, dtype (`int64`, `float64`, `object`), and memory usage. Best for spotting missing values (non-null count < total row count) and unexpected dtypes.
* `df.describe()`: Summary statistics for NUMERIC columns only (skips `object`/string columns automatically); returns `count` (non-null count), `mean`, `std`, `min`, `25%`, `50%` (median), `75%`, `max`.


* **4. Boolean Filtering & Missing Value Detection**
* **Boolean Mask Filtering:**
* Numeric: `filtered_df = df[df["Marks"] > 80]`
* String equality: `it_df = df[df["Department"] == "IT"]`


* **Missing Value Detection & Counting:**
* `df.isnull()` returns a boolean DataFrame (`True` for missing `np.nan` or `None`).
* `df.isnull().sum()` returns missing value count per column (`True` treated as `1`, `False` as `0`).
* `df.isnull().sum().sum()` returns the single grand total of missing cells across the entire DataFrame.





---

## 3. Operations, Methods & Built-In Functions Reference

* `pd.DataFrame(data)`: Builds a DataFrame from dict of lists, list of lists, etc.
* `pd.read_csv(filepath_or_buffer)`: Reads a CSV file into a DataFrame.
* `df.to_csv(path, index=False)`: Exports DataFrame to CSV; pass `index=False` to avoid saving row index column in the CSV.
* `df.head(n=5)` / `df.tail(n=5)`: Preview top/bottom rows.
* `df.info()`: Inspect dtypes, non-null counts, row/col counts, and memory usage.
* `df.describe()`: Compute numeric summary statistics (`count`, `mean`, `std`, `min`, quartiles, `max`).
* `df.dtypes`: Returns a Series of column data types.
* `df.columns.tolist()`: Converts column Index into a plain Python list.
* `df.loc[...]`: Label-based row/column selection (inclusive slice bounds).
* `df.isnull()`: Detects `np.nan` (numeric/normalized) and `None` (string/object) as missing.
* `df.sum()`: Sums values (`df.isnull().sum()` per column; `.sum().sum()` across entire DataFrame).

---

## 4. Keypoints

* **Omitting `index=False` in `df.to_csv()`:** Without `index=False`, Pandas writes the default integer row index (`0, 1, 2, ...`) as an extra column in the CSV; reading it back with `pd.read_csv()` creates an extra/spurious index column.
* **File Path Mismatch Between Write and Read:** Saving to `"data/clean_data.csv"` (subdirectory) and reading from `"clean_data.csv"` (root) causes a file-not-found error; write and read paths must match.
* **`df.describe()` vs. `df.info()` Confusion:** `df.describe()` only summarizes NUMERIC columns (skips `object`/string columns automatically), and its `count` row reflects non-null values (not total rows); `std` is standard deviation (not mean). `df.info()` reports structural metadata (dtypes, non-null counts, memory usage).
* **`NaN` vs. `None` and `float64` Promotion:** Pandas normalizes both `np.nan` and `None` as missing in `df.isnull()` across numeric and string columns (no separate pass needed; avoid raw `== None` or `== np.nan` comparisons). Introducing `NaN` into an integer column promotes its dtype to `float64` because `NaN` is a floating-point representation.
* **Single vs. Double Brackets & Mismatched Dict List Lengths:** `df[["Col1", "Col2"]]` (list inside brackets) selects multiple columns; `df[("Col1", "Col2")]` (tuple inside single brackets) raises a `KeyError`. Forgetting quotes around string column names (`df[Name]`) raises a `NameError`. Passing lists of unequal lengths in a dict to `pd.DataFrame()` raises a `ValueError`.
* **`.loc` Inclusive Slicing & Assignment vs. Equality in Filters:** `df.loc[0:2]` includes index `2` (unlike standard Python `start:stop` which excludes `stop`). Inside a filter, `df[df["Dept"] == "IT"]` uses `==` (not `=`), and filtering returns a filtered view/subset unless reassigned to a variable.
