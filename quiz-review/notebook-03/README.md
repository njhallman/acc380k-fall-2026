[← All quiz reviews](../README.md)

# Quiz review: Notebook 3

These questions revisit function calls, parameters, returned values, local names, defaults, and keyword arguments. Try each one before opening the answer and explanation. Treat each code block as a separate, fresh run.

## 1. Follow a function call

What is displayed after this cell runs?

```python
def mark_for_review(score):
    return score + 5

print(mark_for_review(82))
```

- `83`
- `87`
- `82`
- `27`
- `87.0`

<details>
<summary>Answer and explanation</summary>

**Answer:** `87`

The argument `82` supplies the value of `score`. The function adds `5` and returns the integer `87`, which the outside `print()` displays.

</details>

## 2. Follow the parameters

What does the final print show?

```python
def sequence(first, second):
    return second + " then " + first

route = sequence("collect", "submit")
print(route)
```

- `collect then submit`
- `submit then collect`
- `submit collect`
- `collect`
- `None`

<details>
<summary>Answer and explanation</summary>

**Answer:** `submit then collect`

Python matches these arguments by position: `first` receives `"collect"`, and `second` receives `"submit"`. The expression inside the function puts `second` before `first`. The returned text is stored as `route` and then displayed.

</details>

## 3. Displaying and returning

What is displayed, in order?

```python
def show_total(cost, extra):
    print(cost + extra)

result = show_total(30, 12)
print(result)
```

- `42` only
- `None` only
- `42` then `None`
- `None` then `42`

<details>
<summary>Answer and explanation</summary>

**Answer:** `42` then `None`

The function's `print()` displays `42`. Because the function reaches its end without a `return` statement, it returns `None`. The assignment stores that returned value as `result`, and `print(result)` displays it. Printing a value inside a function does not also return that value.

</details>

## 4. Names inside and outside a function

What happens when the cell runs?

```python
def make_label(code, prefix="INV-"):
    label = prefix + code
    return label

saved_label = make_label("A7")
print(saved_label)
print(label)
```

- It prints `INV-A7` twice.
- It prints `INV-A7`, then `A7`.
- It prints `INV-A7`, then `None`.
- It prints `INV-A7`, then raises `NameError`.

<details>
<summary>Answer and explanation</summary>

**Answer:** It prints `INV-A7`, then raises `NameError`.

The function returns the text `"INV-A7"`, and the calling code stores it as `saved_label`. The first print works. The name `label` is local to the function; returning its value does not create a notebook-level name `label`. The final print therefore raises `NameError`.

</details>

## 5. Defaults and keyword arguments

What do these three lines print?

```python
def add_charges(base, tax_rate=0.08, tip=0.0):
    """Return total with tax and tip."""
    return base * (1 + tax_rate + tip)

print(add_charges(200))
print(add_charges(200, tip=0.10))
print(add_charges(200, 0.05, tip=0.10))
```

- `216.0`, `236.0`, `236.0`
- `216.0`, `230.0`, `230.0`
- `208.0`, `236.0`, `230.0`
- `216.0`, `236.0`, `230.0`

<details>
<summary>Answer and explanation</summary>

**Answer:** `216.0`, `236.0`, `230.0` is the intended choice.

The first call uses both defaults: an 8% tax rate and no tip. The second keeps the default tax rate and sets a 10% tip by keyword. The third supplies a 5% tax rate by position and a 10% tip by keyword. The docstring describes the function but does not change its calculation.

The original answer choices abbreviate the numerical results. The code shown in class does not round, so Python actually displays:

```text
216.0
236.00000000000003
230.00000000000003
```

The extra decimal digits come from floating-point representation, not from different argument matching. Applying `round(..., 2)` to the calculation would produce the shorter values in the intended choice.

</details>

## 6. Reassigning a name inside a function

What happens when the following code is run?

```python
pi = 3.1

def area_calc(r):
    pi = pi + 0.04
    area = pi * r**2
    return area

print(area_calc(1))
```

- `3.14` is displayed
- Nothing is displayed
- `3.1` is displayed
- An error

<details>
<summary>Answer and explanation</summary>

**Answer:** An error (`UnboundLocalError`).

Assigning to `pi` inside the function makes `pi` a local name throughout that function. On the right side of `pi = pi + 0.04`, Python tries to read that local name before it has been assigned a value. It does not use the outside `pi` for that read.

The function stops at that line, so it never calculates or returns an area. The outside `print()` does not get a value to display; Python reports the error instead.

</details>
