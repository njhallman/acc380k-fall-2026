[← All quiz reviews](../README.md)

# Quiz review: Notebook 5

These questions revisit strings, lists, dictionaries, and tuples, along with function calls and decisions from earlier notebooks. Questions 1–5 cover strings; Questions 6–10 cover collections. Try each one before opening the answer and explanation. Treat each code block as a separate, fresh run.

## 1. Read a label

What is displayed, in order?

```python
tag = "Q3-2026"
print(tag[0] + tag[-1])
print(tag[3:7])
```

- `Q6, then -202`
- `Q6, then 2026`
- `Q3, then 2026`
- `Q6, then 202`

<details>
<summary>Answer and explanation</summary>

**Answer:** `Q6, then 2026`

`tag[0]` is `"Q"` and `tag[-1]` is `"6"`, so joining them with `+` gives `"Q6"`. The slice starts at position `3` and stops before position `7`, giving `"2026"`.

</details>

## 2. Clean a label

What is displayed, in order?

```python
raw = "  Red Door  "
cleaned = raw.strip()
cleaned.lower()
cleaned = cleaned.replace(" ", "-")
print(cleaned)
print(raw == cleaned)
```

- `red-door, then False`
- `Red-Door, then True`
- `Red-Door, then False`
- `red-door, then True`

<details>
<summary>Answer and explanation</summary>

**Answer:** `Red-Door, then False`

`.strip()` returns `"Red Door"`, which is saved in `cleaned`. `.lower()` returns a new string, but that result is not saved. `.replace()` then produces `"Red-Door"`. `raw` still contains its original spaces, so `raw == cleaned` is `False`.

</details>

## 3. Search the text

What is displayed, in order?

```python
text = "Audit audit"
print(text.find("audit"))
print(text.lower().find("audit"))
print("AUDIT" in text)
```

- `6, then 0, then False`
- `0, then 0, then False`
- `6, then 6, then False`
- `6, then 0, then True`

<details>
<summary>Answer and explanation</summary>

**Answer:** `6, then 0, then False`

The first lowercase `"audit"` starts at position `6`. In `text.lower()`, the first word also matches, so `.find()` returns `0`. The original text has not changed, and it does not contain the uppercase string `"AUDIT"`.

</details>

## 4. Two search calls

What is displayed, in order?

```python
def locate(text, phrase="fee"):
    position = text.find(phrase)
    if position > 0:
        return "found"
    return "missing"

print(locate("fee due"))
print(locate("late fee"))
```

- `found, then found`
- `found, then missing`
- `missing, then missing`
- `missing, then found`

<details>
<summary>Answer and explanation</summary>

**Answer:** `missing, then found`

Both calls use the default phrase `"fee"`. In `"fee due"`, `.find()` returns `0`, so `position > 0` is `False` and the function returns `"missing"`. In `"late fee"`, `.find()` returns `5`, so the function returns `"found"`. The condition incorrectly excludes a valid match at position `0`.

</details>

## 5. Check a context function

Rule: Return the whole phrase with one character on each side, or "missing" if absent. Which call returns the WRONG result?

```python
def nearby(text, phrase):
    position = text.find(phrase)
    if position == -1:
        return "missing"
    return text[position - 1:position + 2]
```

- `nearby("xAx", "A")`
- `nearby("xBCx", "BC")`
- `nearby("xAx", "Z")`
- `nearby("xABx", "B")`

<details>
<summary>Answer and explanation</summary>

**Answer:** `nearby("xBCx", "BC")`

This call returns `"xBC"`, but the rule requires `"xBCx"`. The fixed stop `position + 2` works for a one-character phrase, not a two-character phrase. To include the whole phrase and one following character, the stop must be `position + len(phrase) + 1`. The other calls return `"xAx"`, `"missing"`, and `"ABx"`, respectively, as required.

</details>

## 6. Read a row

What is displayed, in order?

```python
rows = [
    ["Houston", 6, False],
    ["El Paso", 9, True],
]

print(rows[1][0])
print(rows[0][-1])
```

- `Houston, then False`
- `El Paso, then True`
- `The whole second row, then False`
- `El Paso, then False`

<details>
<summary>Answer and explanation</summary>

**Answer:** `El Paso, then False`

`rows[1]` selects the second list, and the following `[0]` selects its first item, `"El Paso"`. `rows[0]` selects the first list, and `[-1]` selects its final item, `False`.

</details>

## 7. Trace an alias, a copy, and append

What is displayed?

```python
checks = ["amount", "date"]
backup = checks
snapshot = checks.copy()
result = backup.append("vendor")

print(len(checks), len(snapshot), result)
```

- `2 2 None`
- `3 2 None`
- `3 3 None`
- `3 2 ["amount", "date", "vendor"]`

<details>
<summary>Answer and explanation</summary>

**Answer:** `3 2 None`

`backup` and `checks` name the same list, so appending through `backup` makes `checks` contain three items. `snapshot` is a separate copy made before the append and still has two items. `.append()` changes the list and returns `None`, which is saved in `result`.

</details>

## 8. Trace a nearly correct dictionary key

What is displayed, in order?

```python
record = {"region": "West", "units": 8}
alias = record
record["unit"] = 9

print("West" in alias)
print(len(alias))
```

- `True, then 3`
- `False, then 2`
- `False, then 3`
- `True, then 2`

<details>
<summary>Answer and explanation</summary>

**Answer:** `False, then 3`

Dictionary membership tests keys, not values, so `"West" in alias` is `False`. `"unit"` and `"units"` are different keys, so the assignment adds a third key. `alias` names the same dictionary and sees that change.

</details>

## 9. Unpack and reassign a name

What is displayed, in order?

```python
summary = ("West", 8)
region, units = summary
units = 9

print(summary)
print(region, units)
```

- `("West", 8), then West 9`
- `("West", 9), then West 9`
- `("West", 8), then 8 West`
- `A TypeError occurs before anything is displayed`

<details>
<summary>Answer and explanation</summary>

**Answer:** `("West", 8), then West 9`

Unpacking assigns the tuple's first item to `region` and its second item to `units`. The later assignment changes `units` to `9`; it does not change the tuple, which still contains `"West"` and `8`. Python displays the tuple as `('West', 8)`, using single quotes around the same string represented with double quotes in the choice. The second line is `West 9`.

</details>

## 10. Find the discriminating test

Rule: return the smallest and largest values, in that order. Which input proves this candidate is wrong?

```python
def bounds(values):
    return values[0], values[-1]
```

- `[3, 8, 11]`
- `[4, 4]`
- `[5]`
- `[8, 3, 11]`

<details>
<summary>Answer and explanation</summary>

**Answer:** `[8, 3, 11]`

The function returns the first and last items rather than the smallest and largest. For `[8, 3, 11]`, it returns `(8, 11)`, but the rule requires `(3, 11)`. The other three inputs happen to put a smallest value first and a largest value last, so they do not expose the problem.

</details>
