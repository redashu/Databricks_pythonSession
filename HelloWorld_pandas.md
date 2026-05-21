# Pandas: Series vs DataFrame

`Series` and `DataFrame` are the two main data structures in Pandas.

The easiest way to think about them:

- **Series** → Single column
- **DataFrame** → Multiple columns (table)

## Example from Student Data

| Name  | Marks |
|-------|-------|
| Rahul | 80    |
| Priya | 90    |
| John  | 75    |

Here:

- **Marks** alone → `Series`
- Entire table → `DataFrame`

---

## 1. Series

A **Series** is a one-dimensional labeled array.

### Example

```python
import pandas as pd

marks = pd.Series([80, 90, 75])
print(marks)
```

### Output

```text
0    80
1    90
2    75
dtype: int64
```

### Structure

| Index | Value |
|------:|------:|
| 0     | 80    |
| 1     | 90    |
| 2     | 75    |

A Series contains only **one column of data**.

---

## 2. DataFrame

A **DataFrame** is a two-dimensional table with rows and columns.

### Example

```python
import pandas as pd

student_df = pd.DataFrame({
    "Name": ["Rahul", "Priya", "John"],
    "Marks": [80, 90, 75]
})

print(student_df)
```

### Output

```text
    Name  Marks
0  Rahul     80
1  Priya     90
2   John     75
```

### Structure

| Row Index | Name  | Marks |
|----------:|-------|------:|
| 0         | Rahul | 80    |
| 1         | Priya | 90    |
| 2         | John  | 75    |

---

## Key Differences

| Feature     | Series        | DataFrame         |
|-------------|---------------|-------------------|
| Dimension   | 1D            | 2D                |
| Data        | Single column | Multiple columns  |
| Has rows    | Yes           | Yes               |
| Has columns | No            | Yes               |
| Type        | `pd.Series()` | `pd.DataFrame()`  |

---

## Relationship Between Them

A **DataFrame** is basically a collection of **Series** objects.

### Example

```python
import pandas as pd

df = pd.DataFrame({
    "Name": ["Rahul", "Priya"],
    "Marks": [80, 90]
})

print(type(df["Marks"]))
```

### Output

```python
<class 'pandas.core.series.Series'>
```

Notice:

```python
df["Marks"]
```

returns a **Series**.

---

## Layman Example

Think of an Excel file.

### Single Column in Excel

| Marks |
|------:|
| 80    |
| 90    |
| 75    |

→ This is like a **Series**

### Whole Excel Sheet

| Name  | Marks | City   |
|-------|------:|--------|
| Rahul | 80    | Mumbai |
| Priya | 90    | Delhi  |

→ This is like a **DataFrame**

---

## Easy Memory Trick

- **Series** → Single
- **DataFrame** → Full table
