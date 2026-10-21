[← All quiz reviews](../README.md)

# Midterm review: practice questions

These questions revisit types, string slicing and methods, lists and dictionaries, loops, functions that return two values, and DataFrame work with `.loc`, boolean masks, `groupby`, and new columns. None of them are exam questions. Try each one before opening the answer and explanation. Treat each code block as a separate, fresh run.

## 1. Python basics: types

What does this cell display?

```python
x = "5" + "3"
y = int(x) / 2
type(y)
```

- `float`
- `bool`
- `TypeError`
- `str`
- `int`

<details>
<summary>Answer and explanation</summary>

**Answer:** `float`

`"5" + "3"` joins two strings, so `x` is `"53"`, not `8`. `int("53") / 2` uses `/`, which always produces a float, so `y` is `26.5`. A bare `type(y)` on the last line of a cell displays `float`.

</details>

## 2. Strings: slicing

What does this code print?

```python
s = "FY2025-Q3"
print(s[2:6], s[-2:])
```

- `Y202 Q3`
- `2025- -Q3`
- `2025 Q3`
- `2025 3`
- `FY20 Q3`

<details>
<summary>Answer and explanation</summary>

**Answer:** `2025 Q3`

Slicing `s[2:6]` starts at position 2 and stops before position 6, which gives `"2025"`. `s[-2:]` takes the last two characters, `"Q3"`. `print` separates the two values with a space.

</details>

## 3. Strings: methods

What does this code print?

```python
t = "  Net Income  "
print(t.strip().lower().replace(" ", "_"))
```

- `net_income`
- `net income`
- `__net_income__`
- `Net_Income`
- `_net_income_`

<details>
<summary>Answer and explanation</summary>

**Answer:** `net_income`

`strip()` runs first and removes the spaces on both ends, leaving `"Net Income"`. `lower()` gives `"net income"`, and `replace(" ", "_")` changes only the one remaining inner space.

</details>

## 4. Strings: find

What does this code print?

```python
memo = "fee risk"
print(memo.find("risk"), memo.find("tax"))
```

- `5 -1`
- `4 -1`
- `4 ValueError`
- `4 0`
- `5 0`

<details>
<summary>Answer and explanation</summary>

**Answer:** `4 -1`

Positions count from 0: `f` is 0, `e` is 1, `e` is 2, the space is 3, so `"risk"` starts at 4. `.find` returns `-1` when the phrase is not there, rather than raising an error.

</details>

## 5. Lists: append and item assignment

What does this code print?

```python
accts = ["Cash", "AR", "Inventory"]
accts[1] = "Receivables"
accts.append("Prepaid")
print(accts[1], accts[-1], len(accts))
```

- `Cash Prepaid 4`
- `Receivables Prepaid 4`
- `Receivables Inventory 3`
- `AR Prepaid 4`
- `Receivables Prepaid 3`

<details>
<summary>Answer and explanation</summary>

**Answer:** `Receivables Prepaid 4`

`accts[1] = "Receivables"` replaces `"AR"` in place. `append` adds `"Prepaid"` at the end, so `accts[-1]` is `"Prepaid"`. The list now has 4 items.

</details>

## 6. Dictionaries: update and add keys

What does this code print?

```python
bal = {"Cash": 500, "AR": 200}
bal["AR"] = bal["AR"] + 50
bal["AP"] = 75
print("AP" in bal, bal["AR"], len(bal))
```

- `False 250 3`
- `True 250 2`
- `True 250 3`
- `KeyError: 'AP'`
- `True 200 3`

<details>
<summary>Answer and explanation</summary>

**Answer:** `True 250 3`

Assigning to an existing key replaces its value, so `"AR"` becomes `250`. Assigning to a new key adds it, so `"AP"` is now in `bal`, and `bal` has 3 keys.

</details>

## 7. Loops: for with continue

What does this code print?

```python
total = 0
for a in [120, -30, 80, -10, 50]:
    if a < 0:
        continue
    total = total + a
print(total)
```

- `210`
- `290`
- `120`
- `40`
- `250`

<details>
<summary>Answer and explanation</summary>

**Answer:** `250`

`continue` skips the rest of the loop body for the negative amounts, so they are never added. The total is `120 + 80 + 50`, which is `250`.

</details>

## 8. Loops: while

What does this code print?

```python
cash = 1000
years = 0
while cash < 1300:
    cash = cash * 1.1
    years += 1
print(years)
```

- `30`
- `The loop never stops.`
- `2`
- `4`
- `3`

<details>
<summary>Answer and explanation</summary>

**Answer:** `3`

After each pass, `cash` grows to 1100, then 1210, then 1331. The condition `cash < 1300` is checked before each pass, and it is first false after the third year, so the loop stops with `years` equal to `3`.

</details>

## 9. Functions: returning two values

What does this cell display?

```python
def split(total, share):
    mine = total * share
    return mine, total - mine

type(split(10, 0.5))
```

- `float`
- `tuple`
- `str`
- `list`
- `int`

<details>
<summary>Answer and explanation</summary>

**Answer:** `tuple`

`return mine, total - mine` sends back both values together as one tuple, `(5.0, 5.0)`. A bare `type(...)` on the last line of a cell displays `tuple`.

</details>

## 10. pandas: boolean masks

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"dept": ["Tax","Audit","Tax","Audit","Tax"],
    "hours": [10, 4, 6, 8, 2]})
print(len(df.loc[(df["dept"] == "Tax") & (df["hours"] > 3)]))
```

- `3`
- `1`
- `2`
- `5`
- `ValueError`

<details>
<summary>Answer and explanation</summary>

**Answer:** `2`

The mask keeps rows where both conditions are true. The Tax rows have hours 10, 6, and 2, and only 10 and 6 are above 3, so two rows remain.

</details>

## 11. pandas: groupby mean vs sum

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"dept": ["Tax","Audit","Tax","Audit","Tax"],
    "hours": [10, 4, 6, 8, 2]})
by_dept = df[["dept", "hours"]].groupby("dept").mean()
print(by_dept.loc["Tax", "hours"])
```

- `18`
- `6.0`
- `5.0`
- `6`
- `KeyError: 'Tax'`

<details>
<summary>Answer and explanation</summary>

**Answer:** `6.0`

`groupby("dept").mean()` gives one row per department, with the average hours. Tax averages `(10 + 6 + 2) / 3`, and `mean` returns a float, so the result is `6.0`.

</details>

## 12. pandas: mask and column list in .loc

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"firm": ["A", "B", "C", "D"],
    "rev": [5, 9, 2, 7]})
big = df.loc[df["rev"] > 4, ["firm"]]
print(big.shape)
```

- `(4, 1)`
- `(2, 1)`
- `(3, 1)`
- `(3, 2)`
- `(1, 3)`

<details>
<summary>Answer and explanation</summary>

**Answer:** `(3, 1)`

The mask keeps rows where `rev` is above 4: A, B, and D. The column list `["firm"]` keeps only one column, so the shape is `(3, 1)`.

</details>

## 13. pandas: groupby sum

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"region": ["TX", "CA", "TX", "CA"],
    "visits": [3, 5, 4, 1]})
tot = df.groupby("region")["visits"].sum()
print(tot.loc["TX"], tot.loc["CA"])
```

- `3 5`
- `13 13`
- `7 6`
- `3.5 3.0`
- `4 1`

<details>
<summary>Answer and explanation</summary>

**Answer:** `7 6`

`groupby("region")["visits"].sum()` adds the visits within each region. TX is `3 + 4 = 7` and CA is `5 + 1 = 6`, and `.loc` looks each one up by its label.

</details>

## 14. pandas: groupby mean and sort_values

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"region": ["TX", "CA", "TX", "CA"],
    "visits": [3, 5, 4, 1]})
avg = df[["region", "visits"]].groupby("region").mean()
avg = avg.sort_values("visits")
print(avg.reset_index().loc[0, "region"])
```

- `CA`
- `0`
- `3.0`
- `KeyError: 0`
- `TX`

<details>
<summary>Answer and explanation</summary>

**Answer:** `CA`

The averages are 3.0 for CA and 3.5 for TX. `sort_values` puts the smallest first, so after `reset_index` the region in row 0 is `CA`.

</details>

## 15. pandas: new column

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"region": ["TX", "CA", "TX", "CA"],
    "visits": [3, 5, 4, 1]})
df["flag"] = "review"
print(df.shape, df.loc[2, "flag"])
```

- `(4, 3) flag`
- `(4, 3) review`
- `(4, 2) review`
- `(3, 4) review`
- `(5, 3) review`

<details>
<summary>Answer and explanation</summary>

**Answer:** `(4, 3) review`

Assigning a single value to a new column fills every row with that value. The DataFrame still has 4 rows but now has 3 columns, and row 2 holds `"review"`.

</details>

## 16. pandas: groupby on two columns

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"year": [2025, 2025, 2026, 2026, 2026],
    "qtr": [1, 1, 1, 2, 2], "rev": [4, 6, 5, 3, 1]})
g = df.groupby(["year", "qtr"])["rev"].sum().reset_index()
print(len(g), g.loc[2, "rev"])
```

- `5 4`
- `2 4`
- `3 1`
- `3 5`
- `3 4`

<details>
<summary>Answer and explanation</summary>

**Answer:** `3 4`

Grouping on two columns makes one group per (year, qtr) pair: (2025, 1), (2026, 1), and (2026, 2). That is 3 rows, and row 2's total is `3 + 1 = 4`.

</details>
