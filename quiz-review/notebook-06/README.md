[← All quiz reviews](../README.md)

# Quiz review: Notebook 6

These questions revisit loops that keep a running total, count qualifying items, use positions to match two lists, number items with `enumerate`, and collect names from a dictionary. Try each one before opening the answer and explanation. Treat each code block as a separate, fresh run.

## 1. Total with a starting value

What does this code print?

```python
total = 1

for value in [3, 2, 3]:
    total = total + value

print(total)
```

- `8`
- `9`
- `4`
- `6`

<details>
<summary>Answer and explanation</summary>

**Answer:** `9`

The total starts at `1`. The loop adds `3`, then `2`, then the second `3`, so it becomes `4`, then `6`, then `9`. The repeated `3` is visited again.

</details>

## 2. Count qualifying items

What does this code print?

```python
durations = [8, 12, 8, 5]
count = 0

for duration in durations:
    if duration >= 8:
        count = count + 1

print(count)
```

- `1`
- `4`
- `28`
- `3`

<details>
<summary>Answer and explanation</summary>

**Answer:** `3`

Both `8` values and the `12` pass `duration >= 8`; `5` does not. Each qualifying item adds `1` to `count`, not its own value, so the final count is `3`.

</details>

## 3. Match two lists by position

What does this code print?

```python
prices = [4, 7, 3]
quantities = [2, 1, 4]
total = 0

for i in range(len(prices)):
    total = total + prices[i] * quantities[i]

print(total)
```

- `14`
- `13`
- `27`
- `21`

<details>
<summary>Answer and explanation</summary>

**Answer:** `27`

`range(len(prices))` supplies the positions `0`, `1`, and `2`. Each pass multiplies the price and quantity at the same position and adds the product to `total`: `4 * 2 + 7 * 1 + 3 * 4 = 27`.

</details>

## 4. Display numbers and list positions

What does this code print?

```python
labels = ["pen", "pad", "clip"]

for number, label in enumerate(labels, start=1):
    if number == 2:
        print(number, label, labels[number])
```

- `2 pad clip`
- `2 pad pad`
- `1 pad pad`
- `2 clip clip`

<details>
<summary>Answer and explanation</summary>

**Answer:** `2 pad clip`

`enumerate(labels, start=1)` produces the pairs `(1, "pen")`, `(2, "pad")`, and `(3, "clip")`. When `number` is `2`, `label` is `"pad"`. But `start=1` changes only the displayed number, not the list's positions: `labels[2]` is still `"clip"`.

</details>

## 5. Filter a dictionary and collect names

What does this code print?

```python
ratings = {"East": 4, "West": 2, "North": 5}
cutoff = ratings["East"]
ratings["East"] = 3
selected = []

for name, rating in ratings.items():
    if rating >= cutoff:
        selected.append(name)

print(selected)
```

- `['East', 'North']`
- `['North']`
- `[5]`
- `['East', 'West', 'North']`

<details>
<summary>Answer and explanation</summary>

**Answer:** `['North']`

`cutoff` saved the integer `4` before `ratings["East"]` was changed to `3`; changing the dictionary later does not change `cutoff`. The loop sees the current ratings `3`, `2`, and `5`. Only `"North"` is at least `4`, so `append(name)` collects just that name.

</details>
