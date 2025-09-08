# Pandas File I/O: Reading & Writing CSV, Excel, JSON

# Overview

Pandas makes it easy to **read from** and **write to** various file 
formats like CSV, Excel, and JSON.


# Reading Files

```python
# Reading CSV
import pandas as pd

df = pd.read_csv("data.csv")
print(df.head())      # Print first 5 rows

# Reading Excel:
# Requires openpyxl or xlrd package for Excel support:pip 
# install openpyxl
 
df = pd.read_excel("data.xlsx", sheet_name="Sheet1")
print(df.head())

# Reading JSON:
df = pd.read_json("data.json")
print(df.head())

# Writing Files:
df.to_csv("output.csv", index=False)

# Writing to Excel:
df.to_excel("output.xlsx", index=False)

# Writing to JSON:
df.to_json("output.json", orient="records", lines=True)


