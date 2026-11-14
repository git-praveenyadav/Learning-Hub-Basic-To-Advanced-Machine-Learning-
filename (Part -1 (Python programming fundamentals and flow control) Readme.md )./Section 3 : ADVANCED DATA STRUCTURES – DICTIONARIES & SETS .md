# Section 3: Advanced Data Structures – Dictionaries & Sets

**A comprehensive guide covering syntax, core coding concepts, methods, and high-yield exam traps for Python dictionaries, sets, and frozensets.**

---

## 1. Syntax & Construction (Dicts & Sets)
* **Dictionaries (`dict`):** Created using curly brackets `{}` with `key: value` pairs. They map string keys to arbitrary values, mirroring JSON web API object formats.
* **Sets (`set`):** Created using curly brackets `{}` or the `set()` constructor. They maintain unordered, unique elements, automatically eliminating duplicates.
* **Frozen Sets (`frozenset`):** An immutable and hashable version of a set where elements cannot be added or removed post-creation.
* **Memory Allocation:** Tuples and frozensets receive a fixed memory block at creation, whereas lists, dicts, and sets use dynamically growing memory.

---

## 2. Core Coding Concepts & Syntax Patterns
* `student3 = {"name": "Ritesh", "marks": {"math": 54}}`: Nested dictionary structure.
* `student3["marks"]["math"]`: Chained bracket access to reach nested values.
* `student3["marks"]["biology"] = 97`: Adding a new key-value pair via direct assignment.
* `del student3["marks"]["math"]`: Removing an existing key using the `del` keyword.
* `student3["marks"].get("biology", "Not found")`: Safe retrieval avoiding `KeyError`.
* Dictionaries preserve insertion order as a language guarantee in Python 3.7+. Reassigning an existing key silently overwrites the old value.
* `names = {81, 81, 82}`: Duplicate elements are automatically dropped.
* `names.add((1, 2))`: Valid because tuples are immutable and hashable. (Passing lists raises `TypeError` since lists are mutable/unhashable).
* `ai_students | web_students`: Union returns a new set with all elements from both, removing duplicates.
* `ai_students & web_students`: Intersection returns elements present in both sets.
* `ai_students - web_students`: Difference returns elements in the left operand absent from the right.
* `ai_students ^ web_students`: Symmetric difference returns elements in one set or the other, but not both.
* Python treats `True` as equal to `1` and `False` as equal to `0` sharing the same hash value, so adding `True` to a set containing `1` has no effect.

---

## 3. Operations, Methods & Built-In Functions Reference
* `dict.get(key, default)`: Safely returns a value for a key or a default value if absent.
* `dict.keys()`, `dict.values()`, `dict.items()`: Returns view objects (note that `.keys()` only evaluates top-level keys).
* `set.add(val)`: Adds a single element to a set.
* `set.discard(val)`: Safely removes an element; if absent, it does nothing silently without raising an error.
* `set.remove(val)`: Removes an element, raising a `KeyError` if it does not exist.

---

## 4. Keypoints

* **Missing Key Traps (`KeyError`):** Direct bracket lookups (`student3["biology"]`) crash code on non-existent keys. Use `.get()` for graceful fallbacks.
* **Hashability Requirement (`TypeError`):** Dictionary keys and set items must be hashable. Using mutable structures like lists raises a `TypeError`.
* **Empty Set Construction:** `{}` creates an empty dictionary, not a set. Always use `set()` to instantiate an empty set.
* **`.keys()` Scope Limitation:** Calling `.keys()` on a nested dictionary only looks one level deep. You must chain explicitly into sub-dictionaries to query nested keys.
* **`.remove()` vs `.discard()`:** Prefer `.discard()` to prevent runtime crashes caused by `KeyError`s thrown by `.remove()`.
