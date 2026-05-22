# Pandas DataFrame Basics for ML Training

## What is a DataFrame?

A DataFrame is a table-like structure used to store and process data.

It is similar to:

- Excel sheet
- SQL table
- CSV table

## Load Dataset

```python
import pandas as pd

df = pd.read_csv("customer_churn.csv")
```

Explain:

- `pd` -> alias for pandas
- `read_csv()` -> loads CSV file into memory
- `df` -> DataFrame object

## First 5 Records

```python
print(df.head())
```

Output shows:

- first 5 rows
- quick inspection

Trainer point: ML engineers always inspect data before training.

## Last Records

```python
print(df.tail())
```

Useful for:

- checking dataset ending
- corrupted records
- appended data issues

## Dataset Shape

```python
print(df.shape)
```

Example output:

```text
(7043, 21)
```

Meaning:

- 7043 rows
- 21 columns

Explain:

- Rows = observations/customers
- Columns = features

## Column Names

```python
print(df.columns)
```

Useful for:

- feature selection
- preprocessing
- debugging

## Data Types

```python
print(df.info())
```

Very important for ML.

Common types:

- `int64`
- `float64`
- `object`

Example discussion:

- `MonthlyCharges` -> float
- `gender` -> object
- `SeniorCitizen` -> int

ML preprocessing depends heavily on datatype understanding.

## Selecting Columns

### Single Column

```python
print(df['gender'])
```

Explain: returns a Series.

### Multiple Columns

```python
print(df[['gender', 'MonthlyCharges']])
```

Important: use double brackets for multiple columns.

## Statistical Summary

```python
print(df.describe())
```

Includes:

- mean
- std
- min/max
- quartiles

Useful for:

- anomaly detection
- feature scaling
- outlier analysis

## Unique Values

```python
print(df['Contract'].unique())
```

Useful for:

- categorical understanding
- encoding planning

## Value Counts

```python
print(df['Churn'].value_counts())
```

Excellent for:

- class imbalance discussion
- dataset bias

## Filtering Rows

### Example 1: Customers with churn = Yes

```python
print(df[df['Churn'] == 'Yes'])
```

### Example 2: Monthly charges greater than 80

```python
print(df[df['MonthlyCharges'] > 80])
```

Explain: similar to SQL `WHERE` clause.

### AND Condition

```python
print(
    df[
        (df['Churn'] == 'Yes') &
        (df['MonthlyCharges'] > 80)
    ]
)
```

Explain:

- `&` = AND
- parentheses are mandatory

### OR Condition

```python
print(
    df[
        (df['Contract'] == 'Month-to-month') |
        (df['SeniorCitizen'] == 1)
    ]
)
```

## Sorting

```python
print(df.sort_values(by='MonthlyCharges'))
```

Descending:

```python
print(
    df.sort_values(
        by='MonthlyCharges',
        ascending=False
    )
)
```

## Adding New Column

```python
df['YearlyCharges'] = df['MonthlyCharges'] * 12

print(df.head())
```

Excellent example for introducing feature engineering.

## Dropping Columns

```python
df.drop('customerID', axis=1, inplace=True)
```

Explain:

- `axis=1` -> column operation
- `inplace=True` -> modify original DataFrame

Very important ML point: identifiers are usually removed before training.

## Missing Values Check

```python
print(df.isnull().sum())
```

Transition to data cleaning topic.

## Covering iloc Properly

### What is iloc?

`iloc` means integer-location based indexing.

Used to access:

- rows
- columns
- using numeric positions

Syntax:

```python
df.iloc[row_index, column_index]
```

### Example Dataset Understanding

Suppose:

| Index | gender | MonthlyCharges |
|---|---|---|
| 0 | Female | 29.85 |
| 1 | Male | 56.95 |

### Example 1: First Row

```python
print(df.iloc[0])
```

Gets: entire first row.

### Example 2: Specific Cell

```python
print(df.iloc[0, 1])
```

Meaning:

- row 0
- column 1

### Example 3: Multiple Rows

```python
print(df.iloc[0:5])
```

Gets first 5 rows.

### Example 4: Specific Columns

```python
print(df.iloc[:, 0:3])
```

Meaning:

- all rows
- columns 0 to 2

### Example 5: Row + Column Range

```python
print(df.iloc[0:5, 0:4])
```

Gets:

- first 5 rows
- first 4 columns

### Example 6: Last Row

```python
print(df.iloc[-1])
```

Explain: negative indexing is supported.

### Example 7: Last Column

```python
print(df.iloc[:, -1])
```

Useful for target variable extraction.

## Very Important ML Example

### Feature Matrix (X)

```python
X = df.iloc[:, :-1]
```

Meaning: take all columns except last.

### Target Variable (y)

```python
y = df.iloc[:, -1]
```

Meaning: take only last column.

Explain: this is very common in ML pipelines.

## loc vs iloc

| loc | iloc |
|---|---|
| label based | index based |
| column names | numeric positions |

loc example:

```python
print(df.loc[0, 'gender'])
```

iloc example:

```python
print(df.iloc[0, 1])
```

## Best Teaching Strategy

After every example, ask learners:

> What do you think this returns?

This keeps engagement high.

## Real-World Trainer Point

Tell learners:

> In real ML projects, DataFrame manipulation is a daily activity. A large portion of ML engineering work involves:
>
> - selecting features
> - filtering data
> - cleaning rows
> - transforming columns

This gives importance to Pandas beyond syntax.

## Mini Practice Exercises for Learners

### Exercise 1

Show first 10 rows.

Expected:

```python
df.head(10)
```

### Exercise 2

Display only:

- gender
- tenure
- Churn

### Exercise 3

Find customers with:

- `MonthlyCharges > 70`
- `Churn = Yes`

### Exercise 4

Using `iloc`, extract first 3 rows and first 2 columns.
