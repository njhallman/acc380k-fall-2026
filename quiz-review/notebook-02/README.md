[← All quiz reviews](../README.md)

# Quiz review: Notebook 2

These questions revisit values, types, comparisons, Boolean expressions, rounding, stored values, and conversion. Try each one before opening the answer.

## 1. Number versus text

What is displayed after this cell runs?

```python
a = 3
b = a * 2
c = "6"
print(c == b)
```

- `True`
- `False`
- `6`
- `"6"`
- An error

<details>
<summary>Answer and explanation</summary>

**Answer:** `False`

`b` is the integer `6`, while `c` is the string `"6"`. Values with different types are not equal here.

</details>

## 2. Stored comparison results

What does the final line display?

```python
threshold = 20
value = 20
at_or_above = value >= threshold

value = 18
below_now = value < threshold
both_true = at_or_above and below_now

print(value, at_or_above, both_true)
```

- `18 True True`
- `18 False False`
- `20 True False`
- `18 True False`

<details>
<summary>Answer and explanation</summary>

**Answer:** `18 True True`

`at_or_above` stores `True` before `value` changes. After the change, `below_now` is also `True`, so `both_true` is `True`.

</details>

## 3. Comparisons and Boolean operators

What does the final line display?

```python
score = 70
minimum = 70
note_is_missing = True

meets_minimum = score >= minimum
requires_review = (not meets_minimum) or note_is_missing
ready = meets_minimum and (not requires_review)

print(meets_minimum, requires_review, ready)
```

- `True True False`
- `False True False`
- `True False True`
- `True True True`

<details>
<summary>Answer and explanation</summary>

**Answer:** `True True False`

A score equal to the minimum satisfies `>=`. The missing note makes `requires_review` true, so `ready` is false.

</details>

## 4. Division, rounding, and stored values

What do the final two lines display?

```python
raw_value = 456 / 100
rounded_value = round(raw_value, 1)
raw_value = 500 / 100

print(raw_value)
print(rounded_value)
```

- `5.0`, then `4.6`
- `5.0`, then `5.0`
- `4.56`, then `4.6`
- `5.0`, then `4.56`

<details>
<summary>Answer and explanation</summary>

**Answer:** `5.0`, then `4.6`

`rounded_value` stores `4.6` before `raw_value` is reassigned. Changing `raw_value` later does not recalculate the stored rounded value.

</details>

## 5. Find a test that exposes two defects

The intended rule is: flag an item if its value is at least 12 or its label is missing.

```python
proposal_b = (
    (value > 12) or (not label_is_present)
)

proposal_c = (
    (value >= 12) and (not label_is_present)
)
```

Which inputs make the intended rule `True` while both proposals produce `False`?

- `value = 12; label_is_present = True`
- `value = 12; label_is_present = False`
- `value = 13; label_is_present = True`
- `value = 11; label_is_present = False`
- `value = 11; label_is_present = True`

<details>
<summary>Answer and explanation</summary>

**Answer:** `value = 12; label_is_present = True`

The boundary value should trigger the rule even though the label is present. Proposal B wrongly excludes 12, while Proposal C wrongly requires the label to be missing.

</details>

## 6. Convert before combining

After the two assignments run, each labeled line is tested separately. Which line causes an error?

```python
count_text = "8"
extra = 2

print(count_text + str(extra))         # A
print(int(count_text) + extra)         # B
print(int(count_text + extra))         # C
print(str(int(count_text) + extra))    # D
```

- Line A
- Line B
- Line C
- Line D

<details>
<summary>Answer and explanation</summary>

**Answer:** Line C

Line C tries to evaluate `count_text + extra` before `int()` can run. Python cannot add a string and an integer. The other lines convert the necessary value before combining them.

</details>
