[← All quiz reviews](../README.md)

# Midterm review: practice questions

These 16 practice questions were prepared for the Oct 21 Zoom study session. They review the kinds of code-tracing skills the midterm asks for, but none of them are exam questions. Try each one before checking the answer key at the bottom. Treat each code block as a separate, fresh run in a notebook cell; the pandas questions start with `import pandas as pd`.

## 1. Python basics: types

What does this cell display?

```python
x = "5" + "3"
y = int(x) / 2
type(y)
```

- **A.** `float`
- **B.** `bool`
- **C.** `TypeError`
- **D.** `str`
- **E.** `int`

## 2. Strings: slicing

What does this code print?

```python
s = "FY2025-Q3"
print(s[2:6], s[-2:])
```

- **A.** `Y202 Q3`
- **B.** `2025- -Q3`
- **C.** `2025 Q3`
- **D.** `2025 3`
- **E.** `FY20 Q3`

## 3. Strings: methods

What does this code print?

```python
t = "  Net Income  "
print(t.strip().lower().replace(" ", "_"))
```

- **A.** `net_income`
- **B.** `net income`
- **C.** `__net_income__`
- **D.** `Net_Income`
- **E.** `_net_income_`

## 4. Strings: find

What does this code print?

```python
memo = "fee risk"
print(memo.find("risk"), memo.find("tax"))
```

- **A.** `5 -1`
- **B.** `4 -1`
- **C.** `4 ValueError`
- **D.** `4 0`
- **E.** `5 0`

## 5. Lists: append and item assignment

What does this code print?

```python
accts = ["Cash", "AR", "Inventory"]
accts[1] = "Receivables"
accts.append("Prepaid")
print(accts[1], accts[-1], len(accts))
```

- **A.** `Cash Prepaid 4`
- **B.** `Receivables Prepaid 4`
- **C.** `Receivables Inventory 3`
- **D.** `AR Prepaid 4`
- **E.** `Receivables Prepaid 3`

## 6. Dictionaries: update and add keys

What does this code print?

```python
bal = {"Cash": 500, "AR": 200}
bal["AR"] = bal["AR"] + 50
bal["AP"] = 75
print("AP" in bal, bal["AR"], len(bal))
```

- **A.** `False 250 3`
- **B.** `True 250 2`
- **C.** `True 250 3`
- **D.** `KeyError: 'AP'`
- **E.** `True 200 3`

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

- **A.** `210`
- **B.** `290`
- **C.** `120`
- **D.** `40`
- **E.** `250`

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

- **A.** `30`
- **B.** `The loop never stops.`
- **C.** `2`
- **D.** `4`
- **E.** `3`

## 9. Functions: returning two values

What does this cell display?

```python
def split(total, share):
    mine = total * share
    return mine, total - mine

type(split(10, 0.5))
```

- **A.** `float`
- **B.** `tuple`
- **C.** `str`
- **D.** `list`
- **E.** `int`

## 10. pandas: boolean masks

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"dept": ["Tax","Audit","Tax","Audit","Tax"],
    "hours": [10, 4, 6, 8, 2]})
print(len(df.loc[(df["dept"] == "Tax") & (df["hours"] > 3)]))
```

- **A.** `3`
- **B.** `1`
- **C.** `2`
- **D.** `5`
- **E.** `ValueError`

## 11. pandas: groupby mean vs sum

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"dept": ["Tax","Audit","Tax","Audit","Tax"],
    "hours": [10, 4, 6, 8, 2]})
by_dept = df[["dept", "hours"]].groupby("dept").mean()
print(by_dept.loc["Tax", "hours"])
```

- **A.** `18`
- **B.** `6.0`
- **C.** `5.0`
- **D.** `6`
- **E.** `KeyError: 'Tax'`

## 12. pandas: mask and column list in .loc

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"firm": ["A", "B", "C", "D"],
    "rev": [5, 9, 2, 7]})
big = df.loc[df["rev"] > 4, ["firm"]]
print(big.shape)
```

- **A.** `(4, 1)`
- **B.** `(2, 1)`
- **C.** `(3, 1)`
- **D.** `(3, 2)`
- **E.** `(1, 3)`

## 13. pandas: groupby sum

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"region": ["TX", "CA", "TX", "CA"],
    "visits": [3, 5, 4, 1]})
tot = df.groupby("region")["visits"].sum()
print(tot.loc["TX"], tot.loc["CA"])
```

- **A.** `3 5`
- **B.** `13 13`
- **C.** `7 6`
- **D.** `3.5 3.0`
- **E.** `4 1`

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

- **A.** `CA`
- **B.** `0`
- **C.** `3.0`
- **D.** `KeyError: 0`
- **E.** `TX`

## 15. pandas: new column

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"region": ["TX", "CA", "TX", "CA"],
    "visits": [3, 5, 4, 1]})
df["flag"] = "review"
print(df.shape, df.loc[2, "flag"])
```

- **A.** `(4, 3) flag`
- **B.** `(4, 3) review`
- **C.** `(4, 2) review`
- **D.** `(3, 4) review`
- **E.** `(5, 3) review`

## 16. pandas: groupby on two columns

What does this code print?

```python
import pandas as pd

df = pd.DataFrame({"year": [2025, 2025, 2026, 2026, 2026],
    "qtr": [1, 1, 1, 2, 2], "rev": [4, 6, 5, 3, 1]})
g = df.groupby(["year", "qtr"])["rev"].sum().reset_index()
print(len(g), g.loc[2, "rev"])
```

- **A.** `5 4`
- **B.** `2 4`
- **C.** `3 1`
- **D.** `3 5`
- **E.** `3 4`

## Answer key

**1. A** (`float`). "5" + "3" joins text to "53"; int("53") / 2 is true division, giving 26.5, a float. A bare type(y) on the last line of a cell displays float.

**2. C** (`2025 Q3`). Index 2 up to (not including) 6 is "2025"; [-2:] is the last two characters.

**3. A** (`net_income`). strip() removes the outer spaces first, so only the inner space becomes "_".

**4. B** (`4 -1`). .find returns where the first match starts, counting from 0, so "risk" starts at 4 (f=0, e=1, e=2, space=3); a missing phrase returns -1.

**5. B** (`Receivables Prepaid 4`). Assigning to position 1 replaces AR; append adds Prepaid at the end, so [-1] is Prepaid and there are 4 items.

**6. C** (`True 250 3`). Assigning to an existing key replaces its value (AR becomes 250); assigning to a new key adds it, so AP is in bal and there are 3 keys.

**7. E** (`250`). continue skips the negatives; 120 + 80 + 50 = 250.

**8. E** (`3`). 1100, 1210, 1331: the third year is the first at or above 1300.

**9. B** (`tuple`). return mine, total - mine sends back both values together as a tuple, (5.0, 5.0), so the cell displays tuple.

**10. C** (`2`). Tax rows have hours 10, 6, 2; two of them exceed 3.

**11. B** (`6.0`). Tax hours average (10 + 6 + 2) / 3 = 6.0; mean returns a float.

**12. C** (`(3, 1)`). rev above 4 keeps A, B, D (3 rows); the column list keeps only firm (1 column).

**13. C** (`7 6`). TX visits 3 + 4 = 7; CA visits 5 + 1 = 6.

**14. A** (`CA`). Means: CA 3.0, TX 3.5. sort_values sorts smallest first, so after reset_index row 0 is CA.

**15. B** (`(4, 3) review`). Assigning a new column adds a third column with the same value in every row; there are still 4 rows.

**16. E** (`3 4`). Groups are (2025, 1)=10, (2026, 1)=5, (2026, 2)=3+1=4, so 3 rows and row 2 has rev 4.
