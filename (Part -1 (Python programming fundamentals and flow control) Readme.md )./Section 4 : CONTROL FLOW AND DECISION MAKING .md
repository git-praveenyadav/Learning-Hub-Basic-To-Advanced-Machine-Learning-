# Section 4: Control Flow and Decision Making

**A comprehensive guide covering syntax, core coding concepts, operators, and high-yield keypoints for Python conditional branching and decision making.**

---

## 1. Syntax & Construction (Control Flow)
* **Control Flow:** Directs code execution order to deviate from straight-line top-to-bottom flow using conditional checks and branching paths.
* **Conditional Syntax:** Uses `if`, `elif` (else if), and `else` keywords.
  * `if`: Mandatory starting check for the primary condition.
  * `elif`: Optional secondary check evaluated only if preceding conditions failed.
  * `else`: Optional catch-all fallback block that runs if all prior conditions are False.
* **Indentation:** Python relies entirely on whitespace indentation (spaces/tabs) to define code blocks under conditional statements, throwing an `IndentationError` if misaligned.



## 2. Core Coding Concepts & Syntax Patterns

* **1. Safe Dictionary Access Before Decision Making**
```python
  user_data = {"name": "Alice", "age": 25}
  job = user_data.get("job")              # Safely returns None instead of throwing a KeyError
  if job is None:
      pass

```


* **2. Basic Conditional Branching & Evaluation Order**
```python
age = 15
if age < 12:
    ticket_price = 5                    # Skipped because 15 < 12 is False
elif age < 18:
    ticket_price = 10                   # Executes because 15 < 18 is True; remaining blocks ignored
else:
    ticket_price = 15

```


* **3. Logical Operators (`and`, `or`, `not`)**
```python
is_raining = False
has_umbrella = True

if not is_raining or has_umbrella:      # 'not' inverts boolean; 'or' requires at least one side to be True
    can_walk = True

```


* **4. Membership and Identity Operators (`in`, `is`)**
```python
allowed_users = ["Alice", "Bob", "Charlie"]
current_user = "Bob"

if current_user in allowed_users:       # Membership check using 'in'
    access = True

account_status = None
if account_status is None:              # Identity check using 'is' for singletons like None
    status_label = "Unassigned"

```


* **5. Flattening Nested If-Else Statements**
```python
in_stock = True
price = 40

# Flattening deep nesting into a clean single-line condition using 'and'
if in_stock and price < 50:
    action = "Buy the item!"
elif not in_stock:
    action = "Out of stock."
else:
    action = "Too expensive."

```



---

## 3. Operations, Methods & Built-In Functions Reference

* **Comparison Operators:** `==`, `!=`, `<`, `>`, `<=`, `>=` for evaluating values.
* **Logical Operators:**
* `and`: Evaluates to True only if ALL conditions are True.
* `or`: Evaluates to True if AT LEAST ONE condition is True.
* `not`: Inverts the boolean value (True becomes False, and vice versa).


* **Membership Operator:**
* `in`: Efficiently checks if a value exists within collections like lists, sets, or keys of dictionaries.


* **Identity Operator:**
* `is`: Evaluates whether two variables point to the exact same object in memory (crucial for checking `None`).



---

## 4. Keypoints

* **Assignment vs. Equality Operator (`=` vs `==`):** Using single `=` inside an `if` condition attempts variable assignment and throws a `SyntaxError`. Always use the double equals `==` comparison operator to check equality.
* **Checking `None` with `==` vs `is`:** Always use `if var is None:` instead of `== None`. The `is` operator checks object identity safely against the singleton `None` in memory.
* **Independent `if` Statements vs. `elif` Chains:** Using multiple standalone `if` statements forces Python to evaluate every single condition independently, potentially triggering multiple blocks. Using an `elif` chain guarantees that **only one** mutually exclusive block executes, stopping as soon as the first match is found.
* **Boundary Validation & Off-by-One Errors:** When validating numeric inputs (e.g., valid age between 0 and 100 inclusive), use correct boundary logic: `if age < 0 or age > 100:` or `if not (age >= 0 and age <= 100):` to catch out-of-bound errors accurately.
* **Deep Nesting ("Spaghetti Code") Anti-Pattern:** Deeply nested `if` statements make code difficult to trace. Flatten conditions by combining them onto a single line using the `and` operator.

```

```
