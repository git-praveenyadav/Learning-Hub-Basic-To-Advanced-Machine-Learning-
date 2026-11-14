# Section 2: Core Python Data Structures – Lists & Tuples

**A comprehensive guide covering syntax, core coding concepts, methods, and high-yield keypoints for Python lists and tuples.**

---

## 1. Syntax & Construction (Lists vs. Tuples)
* **Lists:** Created with square brackets `[]`. Ordered and **mutable** (can change, add, remove items).
* **Tuples:** Created with parentheses `()`. Ordered and **immutable** (fixed, permanent records once created).
* **Analogy:** 
  * **List:** A numbered train / whiteboard (flexible, coaches can be added/removed).
  * **Tuple:** A printed certificate / locked safe (fixed information, read-only).

---

## 2. Core Coding Concepts & Syntax Patterns

* **1. List Construction & Mutable Methods**
```python
  fruits = ["apple", "banana", "mango"]
  fruits.append("cherry")                 # Adds item to the END
  fruits.insert(1, "orange")              # Inserts at index 1, shifts others right
  fruits.remove("banana")                 # Removes the FIRST occurrence by value
  popped_item = fruits.pop()              # Removes and RETURNS the last item (or index passed)
  fruits.sort()                           # Sorts IN-PLACE in ascending order (modifies original)
  fruits.reverse()                        # Reverses IN-PLACE

```

* **2. Indexing & Slicing (Identical for Lists & Tuples)**
```python
scores = [88, 72, 95, 60, 83]
first_item = scores[0]                  # 88 (Zero-based indexing)
last_item = scores[-1]                  # 83 (Negative index counts from the end)
subset = scores[1:4]                    # [72, 95, 60] (Stop index 4 is EXCLUSIVE)

```


* **3. Tuple Creation & Single-Element Trap**
```python
coordinates = (28.6139, 77.2090)        # Standard multi-item tuple
single_item = (42,)                     # Trailing comma is REQUIRED for single-item tuples!
not_a_tuple = (42)                      # This is just an integer 42 in parentheses

```


* **4. Tuple Unpacking**
```python
lat, lon = coordinates                  # Unpacks elements into individual variables cleanly

```



---

## 3. Operations, Methods & Built-In Functions Reference

* **Built-in Functions:**
* `len(container)`: Returns total number of items.
* `sorted(container)`: Returns a NEW sorted list, leaving the original unchanged.
* `type(val)`: Checks object class (e.g., `<class 'tuple'>`, `<class 'list'>`).


* **List Specific Methods:**
* `.append(val)`, `.extend(iterable)`, `.insert(idx, val)`
* `.remove(val)`, `.pop(idx)`, `.clear()`, `.index(val)`, `.count(val)`
* `.sort()`, `.reverse()`


* **Tuple Specific Methods:**
* `.count(val)`, `.index(val)` *(Tuples only have these two because they are immutable!)*



---

## 4. Keypoints

* **The `.sort()` Return Value Bug (`None`):** `.sort()` sorts a list **in-place** and explicitly returns `None`. Doing `result = scores.sort()` makes `result` equal to `None`, NOT the sorted list.
* **Tuple Immutability (`TypeError`):** Tuples cannot be modified after creation. Trying to assign or change an item (e.g., `coordinates[0] = 19.8760`) raises a `TypeError: 'tuple' object does not support item assignment`.
* **Tuple Unpacking Length Mismatch (`ValueError`):** When unpacking a tuple, the number of variables on the left MUST exactly match the number of items in the tuple. A mismatch raises a `ValueError: too many values to unpack` or `not enough values to unpack`.
* **Single-Element Tuple Trailing Comma:** Writing `(42)` creates an `int`, not a tuple. You must include a comma: `(42,)`.
* **Slicing Exclusivity & Out-of-Range Indexing:** In slicing `scores[1:4]`, index `4` is excluded. Accessing an invalid single index (e.g., `scores[10]`) raises an `IndexError`.
* **Appending a List vs. Extending:** `.append([1, 2])` nests the list as a single element inside the parent list. `.extend([1, 2])` unpacks and appends each item individually.

```

```
