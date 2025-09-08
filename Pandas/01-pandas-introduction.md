#  Pandas Introduction

##  What is Pandas?

**Pandas** is a fast, flexible, and powerful open-source Python library 
for **data manipulation**, **cleaning**, and **analysis**.

🔧 Built on top of **NumPy**  
📊 Used widely in **Data Science**, **Machine Learning**, **Finance**, and 
**ETL pipelines**



##  Key Features

- Tabular data structures using **DataFrames**
- 1D labeled arrays using **Series**
- Easy reading/writing of files (CSV, Excel, JSON)
- Powerful groupby, filtering, reshaping
- Handling missing data, duplicates, and merging


## 📥 Installation

### 📦 Using `pip`:
```bash
pip install pandas

import pandas as pd
import pandas as pd

# Create a Series
s = pd.Series([1, 2, 3])
print(s)

# Create a DataFrame
data = {
    "Name": ["Abhi", "Ravi"],
    "Age": [22, 23]
}
df = pd.DataFrame(data)
print(df)

