# Pandas DataFrames


##  What is a DataFrame?

A **DataFrame** is a 2-dimensional, size-mutable, and heterogeneous 
tabular data structure in Pandas.

- Think of it like a **table in a database** or an **Excel sheet**.
- Contains **rows** and **columns**, each with labels.



## 🔹 Creating DataFrames

### ✅ From a Dictionary

```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [24, 27, 22],
    "City": ["Delhi", "Mumbai", "Bangalore"]
}

df = pd.DataFrame(data)
print(df)

From a List of Lists:
data = [
    ["Alice", 24],
    ["Bob", 27],
    ["Charlie", 22]
]

df = pd.DataFrame(data, columns=["Name", "Age"])
print(df)

From a List of Dictionaries:
data = [
    {"Name": "Alice", "Age": 24},
    {"Name": "Bob", "Age": 27},
    {"Name": "Charlie", "Age": 22}
]

df = pd.DataFrame(data)
print(df)

