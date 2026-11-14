
# Section 1: Introduction to Python & String Manipulation

A concise crash course covering Python fundamentals, dynamic typing, core data types, and string manipulation for data science.

---

## 1. Google Colab & Quick Shortcuts
* **Run cell & stay:** `Ctrl + Enter`
* **Run cell & move below:** `Shift + Enter`
* **Add cell below / above:** `B` / `A` *(when not in edit mode)*
* **Delete cell:** Press `D` twice (`D D`)
* **Convert cell type:** `M` (Text) or `Y` (Code)
> ⚠️ **Runtime Trap:** Inactivity disconnects Colab sessions and wipes unassigned variables. Always re-run from the top.

---

## 2. Variables & Core Data Types
Python is dynamically typed—data types are inferred automatically from the assigned value.
* `course_name = "Data Science"` (String)
* `total_marks = 100` (Integer)
* `passing_score = 60.0` (Float)
* `is_registered = True` (Boolean)

**Key Operators:**
* Floor Division (`//`): Divides and rounds down to the nearest integer.
* Modulo (`%`): Returns the remainder of division.
* Exponentiation (`**`): Raises a number to a power.

---

## 3. String Slicing & Core Methods
Strings are indexed starting from `0` or `-1` backwards.
* **Slicing syntax:** `string[start:stop:step]` (Note: the `stop` index is **exclusive**).
* `text.strip()`: Removes leading and trailing whitespace (essential for cleaning CSV/API data).
* **Case conversion:** `.lower()`, `.upper()`, `.title()`
* **Split & Join:** `text.split(" ")` creates a list of words; `" | ".join(words)` joins them back.
* **f-strings:** `f"Student: {name} | Score: {score:.1f}%"` for clean formatting.

---

## 4. Keypoints
* **String Multiplication vs Length:** `'ha' * 3` evaluates to `'hahaha'`, whereas `len('ha')` evaluates to `2`.
* **Index Out of Bounds:** Accessing invalid indices like `name[-100]` throws an immediate `IndexError` instead of wrapping around.
* **Type Mismatches:** Trying to add an integer and string (`5 + '1'`) throws a `TypeError`. Explicit casting (`str()` or `int()`) is required.
* **Assignment vs Comparison:** Single equals (`=`) assigns values; double equals (`==`) checks boolean equality.
* **Floating-Point Limit:** Due to binary storage limits, `0.1 + 0.2` outputs `0.30000000000000004` rather than exact `0.3`.
