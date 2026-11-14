# Section 2: Core Python Data Structures – Lists & Tuples

**A concise crash course covering Python lists, tuples, mutability, key methods, and keypoints.**

---

## 1. Syntax & Construction (Lists vs. Tuples)
* **Lists (`[]`):** Ordered and **mutable** (flexible; items can be added, modified, or removed).
* **Tuples (`()`):** Ordered and **immutable** (fixed, read-only records once created).
* **Analogy:** List = Whiteboard / Train coaches | Tuple = Printed certificate / Locked safe.

---

## 2. Core Coding Concepts & Syntax Patterns
* `fruits = ["apple", "banana"]`: Standard list declaration.
* `fruits.append("cherry")`: Adds item to the **END**.
* `fruits.insert(1, "orange")`: Inserts at index 1 and shifts remaining items right.
* `fruits.remove("banana")`: Deletes the **FIRST** matching value.
* `popped = fruits.pop()`: Removes and **returns** the last item (or specified index).
* `fruits.sort()` / `fruits.reverse()`: Modifies the list **IN-PLACE**.
* `scores[0]` / `scores[-1]`: Zero-based indexing (0 = first item, -1 = last item).
* `scores[1:4]`: Slicing syntax `[start:stop]` where the stop index `4` is **EXCLUSIVE**.
* `coordinates = (28.61, 77.20)`: Standard multi-element tuple.
* `single_item = (42,)`: Trailing comma is **REQUIRED** for single-element tuples (writing `(42)` creates an `int`).
* `lat, lon = coordinates`: Clean tuple unpacking into separate variables.

---

## 3. Operations & Built-In Functions Reference
* `len(container)`: Returns total element count.
* `sorted(container)`: Returns a **NEW** sorted list without modifying the original.
* `type(val)`: Returns the data type (e.g., `<class 'list'>` or `<class 'tuple'>`).
* **List Methods:** `.append()`, `.extend()`, `.insert()`, `.remove()`, `.pop()`, `.clear()`, `.index()`, `.count()`, `.sort()`, `.reverse()`.
* **Tuple Methods:** `.count()`, `.index()` *(Only these two exist because tuples are immutable)*.

---

## 4. Keypoints

* ⚠️ **1. The `.sort()` Return Value Trap:** `.sort()` operates **in-place** and returns `None`. Doing `result = scores.sort()` sets `result` to `None`.
* ⚠️ **2. Tuple Immutability (`TypeError`):** Modifying elements directly (`tup[0] = 10`) throws `TypeError: 'tuple' object does not support item assignment`. 
* ⚠️ **3. Unpacking Mismatch (`ValueError`):** Left-side variables must match tuple length exactly, otherwise it raises `ValueError: too many values to unpack`.
* ⚠️ **4. Appending vs. Extending:** `.append([1,2])` nests the list inside as 1 item; `.extend([1,2])` unpacks and appends elements individually.
* ⚠️ **5. Index Out of Range (`IndexError`):** Accessing an invalid single index (e.g., `scores[99]`) throws `IndexError`, whereas out-of-bounds slicing handles it gracefully.
