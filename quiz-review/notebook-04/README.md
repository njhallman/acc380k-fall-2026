[← All quiz reviews](../README.md)

# Quiz review: Notebook 4

These questions revisit decisions and boundary tests, along with conversions, stored values, and function calls from earlier notebooks. Try each one before opening the answer and explanation. Treat each code block as a separate, fresh run.

## 1. A boundary and the next line

What is displayed, in order?

```python
items = int("12")

if items > 12:
    print("large")
else:
    print("small")

print("done")
```

- `large, then done`
- `small, then done`
- `small only`
- `done only`

<details>
<summary>Answer and explanation</summary>

**Answer:** `small, then done`

`int("12")` produces the integer `12`. The comparison `12 > 12` is `False`, so the `else` block prints `small`. The final `print()` is outside the decision and prints `done`.

</details>

## 2. Two decisions use the current value

What is displayed, in order?

```python
points = 18

if points >= 15:
    points = points - 5

if points >= 15:
    print("A")
else:
    print("B")

print(points)
```

- `A, then 13`
- `A, then 18`
- `B, then 13`
- `A, then B, then 13`

<details>
<summary>Answer and explanation</summary>

**Answer:** `B, then 13`

The first `if` changes `points` from `18` to `13`. The second `if` is a new decision and uses `13`, so its condition is `False` and its `else` prints `B`. The final `print()` displays `13`.

</details>

## 3. Follow the selected branch

What is displayed, in order?

```python
def label(score):
    if score >= 80:
        print("high")
    elif score >= 60:
        return "middle"
    else:
        return "low"

print(label(85))
print(label(70))
```

- `high, then None, then middle`
- `high, then high, then middle`
- `high, then middle`
- `high, then low, then middle`

<details>
<summary>Answer and explanation</summary>

**Answer:** `high, then None, then middle`

For `85`, the first branch prints `high`. Python skips the remaining branches in that chain. The function then reaches its end without executing a `return`, so it returns `None`; the outside `print(label(85))` displays that returned value. For `70`, the `elif` branch returns `middle`, which the second outside `print()` displays.

</details>

## 4. A saved result and a new call

What does the final print display?

```python
def adjusted(score, bonus=5):
    if score < 80:
        score = score + bonus
    return score

score = 78
saved = adjusted(score)
score = 80
print(saved, adjusted(score, bonus=10))
```

- `83 90`
- `80 80`
- `78 80`
- `83 80`

<details>
<summary>Answer and explanation</summary>

**Answer:** `83 80`

The first call receives `score=78` and uses the default `bonus=5`, so `saved` stores `83`. Assigning `80` to the outside name `score` does not change `saved`. The later call receives `score=80` and `bonus=10`. Because `80 < 80` is `False`, it skips the `if` block and returns `80`.

</details>

## 5. Choose a test

Rule: 90 or more → honors; 60 to below 90 → pass; below 60 → retry. Which score makes BOTH functions return the wrong label?

```python
def band_a(score):
    if score >= 60:
        return "pass"
    elif score >= 90:
        return "honors"
    return "retry"

def band_b(score):
    if score > 90:
        return "honors"
    elif score >= 60:
        return "pass"
    return "retry"
```

- `60`
- `90`
- `91`
- `59`

<details>
<summary>Answer and explanation</summary>

**Answer:** `90`

At `90`, the rule requires `honors`, but both functions return `pass`. `band_a` checks the lower threshold first, so its first branch also catches scores of 90 or more. `band_b` uses `> 90`, excluding exactly `90` from its top branch. At `91`, only `band_a` is wrong. At `60` and `59`, both functions agree with the rule.

</details>
