# Part 5: Iteration and Loop Mastery

**A comprehensive guide covering syntax, iteration concepts, loop control statements, and high-yield keypoints for Python for-loops and while-loops.**

---

## 1. Syntax & Construction (Iteration & Loops)

* **Iteration:** The automated process of executing a block of code repeatedly across a collection or until a condition changes.


* **For Loop:** Walks through a fixed collection (list, tuple, set, dict, string, range), automatically running once per element.


* Syntax: `for variable in iterable:`


* **While Loop:** Condition-driven loop that keeps executing as long as a specified boolean condition remains True (used when iteration count is unknown).


* Syntax: `while condition:`


* **Loop Control Keywords:**
* `break`: Immediately exits/terminates the innermost enclosing loop entirely.


* `continue`: Skips the remainder of the current iteration and jumps to the next step.





---

## 2. Core Coding Concepts & Syntax Patterns

* **1. Iterating Over Strings and Collections**
```python
for char in "Python":                   # Yields one character per iteration: 'P', 'y', 't'...
    pass

```


* **2. Iterating Over Dictionaries Using `.items()` and Tuple Unpacking**
```python
salaries = {"Engineer": 50000, "Designer": 75000}
for name, salary in salaries.items():   # Simultaneously unpacks key-value pairs
    print(f"{name} earns {salary}")

```


* **3. Using `range()` and `len()` to Track Index Positions**
```python
users = ["Alice", "Bob", "Charlie"]
for i in range(len(users)):             # len(users) is 3; range(3) produces 0, 1, 2
    print(i, users[i])                  # Accesses both index and value safely

```


* **4. Range Bounds (Start inclusive, Stop exclusive)**
```python
for num in range(3, 7):                 # Produces integers 3, 4, 5, 6 (7 is excluded)
    pass

```


* **5. While Loop with Battery Drain / Threshold Monitoring & break**
```python
power = 5
while power > 0:
    if power <= 2:
        print("Closing all apps.")
        break                           # Exits loop immediately when threshold is hit
    print(f"Power: {power}%")
    power -= 1                          # Crucial update to prevent infinite loops

```


* **6. Using continue to Skip Specific Iterations**
```python
ages = [25, 0, 30, 0, 18]
for age in ages:
    if age == 0:
        continue                        # Skips the rest of this iteration when invalid
    print(f"Processing age: {age}")

```



---

## 3. Operations, Methods & Built-In Functions Reference

* `range(start, stop, step)`: Generates a sequence of integers from start (inclusive) to stop (exclusive). Does not store a full list in memory.
* **Dictionary Iteration Methods:**
* `.keys()`: Iterates over dictionary keys only.
* `.values()`: Iterates over dictionary values only.
* `.items()`: Returns `(key, value)` tuples, enabling simultaneous destructuring.


* `len(iterable)`: Returns the number of items in a collection, often combined with `range()`.
* **Control Statements:**
* `break`: Terminates the loop execution immediately.


* `continue`: Skips to the next iteration step.





---

## 4. Keypoints

* **Dictionary Default Iteration Trap:** Iterating directly over a dictionary (`for item in dict:`) iterates over its **keys only**, not values or pairs. Always use `.items()` when both key and value are needed.
* **Passing a List into range() (`TypeError`):** `range(users)` raises a `TypeError` because `range()` expects integer arguments, not list objects.
* **Comparing Whole Collections vs. Individual Elements:** Writing `for order in orders:` with an inline condition works per element, whereas attempting `orders >= 500` compares the entire list object against an integer.
* **Inefficient Constant Computation Inside Loops:** Placing invariant calculations (e.g., `600000 / 12`) inside a loop body causes Python to recalculate the exact same static value on every single iteration, wasting CPU cycles. Compute constants outside the loop.
* **Infinite `while` Loops (Missing Variable Updates or Misplaced `continue`):** Forgetting to update the loop control variable inside a `while` loop (or placing a `continue` before the variable update) keeps the condition permanently True, resulting in an infinite loop.
