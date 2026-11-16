# Section 6: Functional Programming for Reusability

A comprehensive guide covering syntax, function definition, the DRY principle, function composition, and high-yield exam traps for Python functions.

---

## 1. Syntax & Construction (Functions & Reusability)

* **User-defined functions:** Packaged, reusable blocks of code that only execute when specifically called by their name.


* **Function Definition:** Defined using the `def` keyword, followed by a custom function name, parentheses `()` containing parameters, and a colon `:`.


* **Indentation:** Python uses strict indentation rules instead of curly braces `{}` to define the function body block.
* **Return Statement:** Acts as both a delivery mechanism (sending computed values back to the caller) and an immediate exit point.

---

## 2. Core Coding Concepts & Syntax Patterns

* **1. Defining and Calling Basic Functions**
```python
def add_shipping_cost(item_price):
    final_price = item_price + 5      # Adds fixed shipping fee
    return final_price                # Hands the answer back to the caller

book_total = add_shipping_cost(10)      # Calling the tool with argument 10

```


* **2. The DRY Principle (Don't Repeat Yourself)**
* Writing logic once inside a function and calling it multiple times prevents copy-paste errors and establishes a single source of truth.


* Example: Reusing a centralized `add()` helper function inside broader calculations like company salary averages rather than rewriting loops.


* **3. Initialization Pattern and Augmented Assignment**
```python
def calculate_total(values):
    answer = 0                        # Empty bucket starts at zero before loop
    for val in values:
        answer += val                 # Shorthand for answer = answer + val
    return answer

```


* **4. Function Composition**
* Function composition chains smaller, single-purpose functions together where the output of one function feeds directly as input into another.


* **5. Constants Outside Functions**
* Defining static thresholds or constants outside function bodies ensures they are computed once and makes policy updates manageable.



---

## 3. Operations, Methods & Built-In Functions Reference

* `def`: Keyword that informs Python a new reusable tool is being defined.


* `return`: Keyword that stops execution and outputs the final result.


* `print()`: Displays text or values on the screen and discards them, implicitly returning `None` to the calling environment.
* `sum()`: Built-in function that accepts a list of numbers and returns their total sum.
* `enumerate()`: Wraps any iterable to yield simultaneous `(index, value)` pairs.
* `range(start, stop, step)`: Generates numerical sequences with custom step increments or decrements.
* `dict.items()`: Extracts key-value pairs as tuples during dictionary iteration.

---

## 4. Keypoints

* **Missing `return` Statement Yields `None`:** If a function performs operations or prints internally but lacks a `return` statement, assigning its function call to a variable evaluates to `None`.
* **Confusing `print()` with `return` in Composable Pipelines:** Using `print()` inside helper functions displays results on the screen but discards the data, making it unavailable to downstream callers or pipelines.
* **Applying `enumerate()` to Dictionaries:** Running `enumerate()` on a dictionary yields numeric indices alongside the dictionary's keys, not its values or key-value pairs.
* **Function Scope and Parameters:** Parameters declared inside a function's parentheses behave as local variables, bound to whatever arguments are passed at call time.
* **Choosing Appropriate Loop Constructs:** Use `for` loops when iterating over a fixed, known collection at runtime; use `while` loops for event-driven stopping conditions when iteration counts are unknown in advance (e.g., searching until a condition is met); use `continue` to skip specific malformed or negative records; and use `break` for immediate termination when critical safety or limit thresholds are reached.
