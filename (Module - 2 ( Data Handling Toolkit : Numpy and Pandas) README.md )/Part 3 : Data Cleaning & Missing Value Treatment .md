# Part 3: Data Cleaning & Missing Value Treatment

**A comprehensive guide covering missing value detection and imputation, string and type cleaning, duplicate handling, data cleaning pipelines, and high-yield keypoints.**

---

## 1. Syntax & Construction (Cleaning, Imputation & Parsing)

* **Detecting & Quantifying Missing Values:**
* `df.isnull()` -> Boolean table (`True` for missing `np.nan` / `None`, `False` otherwise).
* `df.isnull().sum()` -> Missing count per column (`True` = `1`, `False` = `0`).
* `df.isnull().sum().sum()` -> Total missing cells across the entire DataFrame.
* `(df.isnull().sum() / len(df)) * 100` -> Percentage of missing values per column.


* **Dropping vs. Filling Missing Values:**
* `df.dropna()` -> Drops rows containing any missing value (best for large datasets with low missingness).
* `df["col"].fillna(value)` -> Replaces missing values with a scalar/substitute:
* Numeric column (small dataset / many nulls): fill with column median (`np.median(...)` / `.median()`).
* Categorical/string column: fill with `"unknown"` (`df["city"].fillna("unknown")`).
* Date column: fill `NaT` with a sentinel date (`df["date"].fillna(pd.to_datetime("1900-01-01"))`).




* **String Cleaning & Type Conversion:**
* `df["col"].astype(str).str.strip().str.title()` -> Casts to string, trims whitespace, and formats title case.
* `df["salary"].astype(str).str.replace("₹", "", regex=False).str.replace(",", "", regex=False)` -> Strips currency/punctuation literals cleanly.
* `pd.to_numeric(series, errors="coerce")` -> Converts to numeric; unparseable strings become `NaN`.
* `pd.to_datetime(series, errors="coerce", dayfirst=True)` -> Parses mixed dates; unparseable entries become `NaT`.
* `df["age"].astype(int)` -> Casts numeric column to integer after all `NaN` values are resolved.


* **Duplicate Handling & Clean Assembly:**
* `df.duplicated()` -> Boolean Series marking duplicate rows (`True` for repeats).
* `df.drop_duplicates()` -> Removes duplicate rows, keeping the first occurrence.
* `clean_df = pd.DataFrame({...})` -> Reassembles cleaned columns while leaving raw data untouched.



---

## 2. Core Coding Concepts & Syntax Patterns

* **1. Four Messy Data Categories & ML Failure Modes**
* **Missing values (`NaN`, `None`, blank cells):** Can crash algorithms or raise type errors; even a bare blank cell (not `NaN`) can halt a long training run without signaling missingness properly.
* **Wrong / inconsistent formats (`"twenty"` in int col, mixed date formats):** Causes casting errors or mixed-type failures.
* **Duplicate rows:** Causes overfitting—the model memorizes repeated rows instead of generalizing patterns.
* **Extra spaces & junk symbols (`"₹45,000"`, `"$50000"`, leading/trailing spaces):** Forces numeric columns to `object` dtype, blocking arithmetic/sorting.


* **2. Cleaning Pipeline Order & Validation**
* **Workflow:** Inspect (`head`, `shape`, `info`, `describe`) -> Measure nulls (`isnull().sum()`) -> Choose strategy (`dropna()` vs `fillna()`) -> Clean strings/types/dates -> Deduplicate (`drop_duplicates()`) -> Assemble & Validate.
* **Validation Checks:** `clean_df.isnull().sum()` (all `0`s), `clean_df.info()` (`int64`/`float64` where expected), `clean_df.describe()` (sensible ranges), and `clean_df["salary"].mean()` (returns a float rather than failing).


* **3. `NaN` vs. `None` vs. `NaT` and `float64` Promotion**
* Numeric missing values are `NaN` (`np.nan`, a float); string/object missing values may appear as `None`; datetime missing values are `NaT`.
* Any numeric column with even one `NaN` is stored/promoted as `float64`; convert to `int` only AFTER filling all `NaN`s.
* Non-standard strings like `"Not Available"` or `"None"` are NOT auto-converted to `NaN` when loading CSVs—they stay as strings (`object` dtype) until converted via `pd.to_numeric(..., errors="coerce")` or `fillna()`.



---

## 3. Operations, Methods & Built-In Functions Reference

* `df.isnull()` / `df.isnull().sum()` / `df.isnull().sum().sum()`: Detect and count missing values.
* `df.dropna()`: Drop rows with any missing value.
* `df.fillna(value)`: Impute missing cells (`NaN`, `None`, `NaT`) with median, `"unknown"`, or a sentinel date.
* `df.duplicated()` / `df.drop_duplicates()`: Detect duplicate rows and drop repeated records.
* `s.astype(dtype)`: Cast Series/column type (e.g., `str`, `int`, `float`).
* `s.str.strip()` / `s.str.title()`: Remove surrounding whitespace and convert to title case.
* `s.str.replace(pat, repl, regex=False)`: Literal substring replacement without regex interpretation.
* `pd.to_numeric(s, errors="coerce")`: Convert to numeric; unparseable strings become `NaN`.
* `pd.to_datetime(s, errors="coerce", dayfirst=True)`: Parse dates; unparseable entries become `NaT`.
* `np.median(arr)` / `s.median()`: Compute median (ignore nulls when computing).

---

## 4. Keypoints

* **Dropping Too Much Data on Small Datasets:** Dropping 80 rows out of 500 (16%) loses too much information; use `fillna(median)` for numeric columns (robust to outliers) or `fillna("unknown")` for categorical columns instead.
* **Putting `"unknown"` in a Numeric Column or Dropping/Replacing Wrongly:** Filling numeric `age` with `"unknown"` corrupts the column into string/object dtype and blocks math. Calling `replace("unknown")` without specifying target/replacement value is not a valid replacement call.
* **String `"None"` / `"Not Available"` vs. Actual Missing Values:** In CSVs/strings, `"Not Available"` or `"None"` is preserved as a string (`object` dtype) and is not automatically converted to `NaN` on load; `pd.to_numeric(..., errors="coerce")` converts strings like `"None"` or `"Not Available"` into `NaN` instead of raising a `ValueError`.
* **Chained String Method Order (`.str.strip()` vs. `.str.title()`):** In `df["department"].astype(str).str.strip().str.title()`, `"  IT  "` first strips to `"IT"`, and then `.str.title()` converts it to `"It"` (first letter uppercase, rest lowercase).
* **Forgetting `regex=False` in `.str.replace()` or Casting to `int` Before Filling `NaN`s:** Always pass `regex=False` when stripping currency/punctuation characters literally. Calling `.astype(int)` while `NaN` values still exist fails/errors; fill `NaN`s first.
* **Over-generalizing Failure Modes in MCQs:** `NaN` values do NOT crash every Pandas operation before training (e.g., `describe()` and `isnull()` run with `NaN`s), and sequential IDs like `employee_id` are not automatically a messy-data format issue to drop carelessly as a feature.
