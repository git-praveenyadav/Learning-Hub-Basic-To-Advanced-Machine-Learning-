# Part 3: Advanced Data Structures – Dictionaries & Sets

**A comprehensive guide covering syntax, core coding concepts, methods, and high-yield Keypoints for Python dictionaries, sets, and frozensets.**

---

## 1. Syntax & Construction (Dicts & Sets)

* **Dictionaries (`dict`):** Created using curly brackets `{}` with `key: value` pairs. They map descriptive string keys (like `"name"` or `"math"`) to arbitrary Python values, corresponding closely to JSON object syntax used in modern web APIs.
* **Sets (`set`):** Created using curly brackets `{}` or the `set()` constructor. They store unordered, unique elements, automatically eliminating duplicates.
* **Frozen Sets (`frozenset`):** An immutable and hashable version of a set where elements cannot be added or removed after creation.
* **Memory Allocation Behavior:** Tuples and frozensets receive a fixed memory block at creation because their element count is immutable. Conversely, lists, dicts, and sets use dynamically growing memory because their contents can expand or shrink over time.

---

## 2. Core Coding Concepts & Syntax Patterns

* **1. Dictionary Construction, Nested Access & Modification**
```python
student3 = {
    "name": "Ritesh",
    "marks": {
        "math": 54,
        "English": 36,
        "physics": 41
    }
}
math_score = student3["marks"]["math"]      # Chained bracket access to reach nested values
student3["marks"]["biology"] = 97           # Adding a new key-value pair via direct assignment
del student3["marks"]["math"]               # Removing an existing key entirely using the `del` keyword
safe_lookup = student3["marks"].get("biology", "Subject marks not found") # Safe retrieval avoiding KeyError

```


* **2. Dictionary Insertion Order & JSON Compatibility**
* As of Python 3.7+, dictionaries preserve insertion order as a language guarantee.
* Re-assigning an existing key (`student3["marks"]["English"] = 63`) silently overwrites the old value.


* **3. Sets Construction & Uniqueness Rules**
```python
names = {81, 81, 82, 84}                    # Duplicate elements are silently dropped (evaluates to {81, 82, 84})
names.add((1, 2))                           # Successful: Tuples are immutable and hashable
# names.add([3, 4])                         # Raises TypeError: unhashable type: 'list' (lists are mutable)

```


* **4. Set Operations & Boolean Equivalence**
```python
ai_students = {"Rahul", "Arushi", "Amit"}
web_students = {"Amit", "Neha", "Rahul"}

union_set = ai_students | web_students      # Returns new set containing all elements from both sets, removing duplicates
inter_set = ai_students & web_students      # Intersection (&): returns elements present in both sets (e.g., {"Rahul", "Amit"})
diff_set = ai_students - web_students       # Difference (-): returns elements in left operand absent from right (e.g., {"Arushi"})
sym_diff = ai_students ^ web_students       # Symmetric difference (^): returns elements in one set or the other, but not both

```


* Python treats `True` as equal to `1` and `False` as equal to `0` sharing the same hash value.
* Adding `True` to a set already containing `1` has no effect because duplicate hash values are dropped.



---

## 3. Operations, Methods & Built-In Functions Reference

* **Dictionary Methods:**
* `.get(key, default)`: Safely returns the value for a key if it exists, or returns the default value if absent.
* `.keys()`, `.values()`, `.items()`: Returns view objects. Note that `.keys()` only evaluates top-level keys.


* **Set Mutation & Safe Removal Methods:**
* `.add(val)`: Adds a single element to a set.
* `.discard(val)`: Safely removes an element; if the value is absent, it does nothing silently (no error).
* `.remove(val)`: Removes an element; raises a `KeyError` if the value does not exist.



---

## 4. Keypoints

* **Square Brackets vs `.get()` on Missing Keys (`KeyError`):** Using direct bracket access (`student3["marks"]["biology"]`) on a non-existent key raises a `KeyError` and crashes code. Use `.get()` to handle missing keys gracefully with a fallback message.
* **Hashability & Unhashable Types (`TypeError`):** Dictionary keys and set items must be **hashable** (immutable types like strings, numbers, tuples). Passing mutable structures like lists or dictionaries as set items or dict keys raises a `TypeError`.
* **Empty Set Construction (`{}` vs `set()`):** Writing `{}` creates an empty dictionary, not an empty set. Always use `set()` to instantiate an empty set.
* **`.keys()` Scope Limitation:** Calling `.keys()` on a nested dictionary only looks one level deep (top-level keys). To query nested keys, you must explicitly chain down to the sub-dictionary (e.g., `student3["marks"].keys()`).
* **Set `.remove()` vs `.discard()` Error Handling:** Always prefer `.discard()` when unsure if an item exists to prevent runtime crashes caused by `KeyError`s thrown by `.remove()`.
