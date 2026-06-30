


# 🐼 Pandas - Complete Mastery: From Data Frames to Analytics Pipeline  

Welcome to the structured notes and assignments repository for the **Pandas** series[cite: 22, 24, 25, 26, 28]. This document serves as a comprehensive, beginner-friendly guide covering core tabular structures, data scrubbing mechanics, conditional queries, structural connections, relational merges, and advanced time series resampling pipelines[cite: 22, 24, 25, 26, 28, 30, 32].

---

## 📋 Table of Contents

* [What is Pandas and Why Use It?](#1-what-is-pandas-and-why-use-it)
* [Installing & Importing Pandas](#2-installing--importing-pandas)
* [Understanding Series vs. DataFrames](#3-understanding-series-vs-dataframes)
* [Data Structural Setup & Creation](#4-data-structural-setup--creation)
  * [Creating a Series](#a-creating-a-series)
  * [DataFrame from Dictionaries](#b-creating-a-dataframe-dictionary-setup)
  * [DataFrame from Nested Row Lists](#c-creating-a-dataframe-nested-row-lists)
  * [DataFrame from NumPy Arrays](#d-creating-a-dataframe-random-numpy-matrices)
* [Data Inspection Blueprint](#5-data-inspection-blueprint)
* [Data Selection & Slicing (`.loc` vs `.iloc`)](#6-data-selection--slicing-loc-vs-iloc)
* [The Data Cleaning Engine](#7-the-data-cleaning-engine)
* [Boolean Indexing & The Logical Bouncer](#8-boolean-indexing--the-logical-bouncer)
* [Descriptive Statistics & Value Frequencies](#9-descriptive-statistics--value-frequencies)
* [The Split-Apply-Combine Workflow (`groupby`)](#10-the-split-apply-combine-workflow-groupby)
* [Structural Combinations (`concat`, `merge`, & `join`)](#11-structural-combinations-concat-merge--join)
* [Working with Time Series Data](#12-working-with-time-series-data)
* [Summary](#13-summary)
* [📂 Homework & Lab Assignment Directory](#-homework--lab-assignment-directory)

---

## 1. What is Pandas and Why Use It?

**Pandas** is the foundational open-source Python library optimized for fast, flexible, and expressive data analysis and manipulation[cite: 4, 22].

* **Duffel Bag vs. Spreadsheet:** While standard Python lists act like flexible duffel bags storing chaotic, mixed data types, Pandas converts your messy information into clean, labeled, rectangular spreadsheets[cite: 4, 22].
* **Tabular Simplicity:** Designed to make working with labeled database schemas, relational tables, and Excel matrix formats intuitive and human-readable[cite: 4, 22].
* **Downstream Integration:** Seamlessly handles the middle pipeline, transforming raw arrays from NumPy into highly-formatted inputs ready for machine learning libraries like Scikit-Learn[cite: 4, 22].

---

## 2. Installing & Importing Pandas

To install the package dependency to your localized system environment, execute the following terminal command[cite: 4, 22]:

```bash
pip install pandas

```

Once installed, include it within your project source code using the standard community-adopted alias:

```python
import pandas as pd

```

---

## 3. Understanding Series vs. DataFrames

Pandas architecture organizes data elements cleanly by splitting dimensional structures:

| Structure | Dimensionality | Description / Analogy |
| --- | --- | --- |
| **Series** | 1D Labeled Array | A single column of data equipped with row labels (like one standalone column in Excel).|
| **DataFrame** | 2D Rectangular Table | A full rectangular tabular grid structured via matching rows and named columns (like a complete spreadsheet).|

---

## 4. Data Structural Setup & Creation

### A. Creating a Series

A 1D Series can be instantiated out of core Python lists or dictionaries while optionally attaching custom row indicator keys.

```python
# Instantiating a 1D Series with player names as row labels
marks = pd.Series([30, 40, 50, 60, 70],
                  index=['Ronaldo', 'Messi', 'Virat', 'Dhoni', 'Mbappe'])
print(marks)

```

### B. Creating a DataFrame (Dictionary Setup)

When converting standard Python dictionaries, dictionary keys automatically resolve as your column names, while array lists stack downwards into matching row index locations.

```python
# Mapping tracking lists into an organized data table schema
info = pd.DataFrame({
    'Name': ['Rahul', 'Devraj', 'Abhishek', 'Rishi'],
    'Age': [20, 21, 22, 20],
    'Marks': [100, 80, 70, 85]
})
print(info)

```

### C. Creating a DataFrame (Nested Row Lists)

Construct tabular data row-by-row by explicitly stacking multiple list arrays inside an outer wrapper list and mapping field headers using the `columns` parameter.

```python
# Constructing historical rows step-by-step
information = pd.DataFrame([
    ['Rahul', 52, 80],
    ['Devraj', 22, 85],
    ['Abhishek', 60, 55]
], columns=['Name', 'Age', 'Marks'])
print(information)

```

### D. Creating a DataFrame (Random NumPy Matrices)

Directly convert multi-dimensional raw numbers generated via NumPy's random distributions into clean, column-labeled data frame views.

```python
import numpy as np

# Generates a 3x4 layout packed with random values from 1 to 99
arr = np.random.randint(1, 100, size=(3, 4))
arr_df = pd.DataFrame(arr, columns=['A', 'B', 'C', 'D'])
print(arr_df)

```

---

## 5. Data Inspection Blueprint

Before processing your dataset, run these metadata methods to quickly inspect the structure of your tabular coordinates:

```python
# Create a small DataFrame view for tracking attributes
df = pd.DataFrame({
    "Name": ["Alice", "Bob", "Charlie", "David", "Emma"],
    "Age": [25, 30, 35, 40, 22],
    "Score": [88, 92, 79, 85, 95]
})

print(df.head(3))   # (.head) Peeks at the first 3 rows from the top[cite: 20, 24]
print(df.tail(2))   # (.tail) Peeks at the last 2 records from the bottom[cite: 24]
print(df.shape)     # (.shape) Blueprint dimensions -> Returns (rows, columns): (5, 3)[cite: 24]
print(df.dtypes)    # (.dtypes) Material array type inside each column[cite: 24]
df.info()           # (.info) Complete system health summary (Non-null counts, types)[cite: 24]

```

---

## 6. Data Selection & Slicing (`.loc` vs `.iloc`)

Target and query smaller data segments by choosing between clear text row labels or positional index counters.

### `.loc` — Label-Based Coordinate Pointer

* **Real-World Analogy:** Explicit directions. You command the engine to find the intersection labeled explicitly with row index `1` and column string name `"Name"`.



```python
# Extract the exact item at matching text coordinates
print(df.loc[1, 'Name'])  # Returns: 'Bob'[cite: 24]

```

### `.iloc` — Integer-Based Coordinate Indexer

* **Real-World Analogy:** Index-only floor coordinates. Bypasses text labels completely, pulling items using standard sequential integer counting windows `[start:stop]`.



```python
# Crop out row positions 0 to 1 and the first two columns (stop value is exclusive)
print(df.iloc[0:2, 0:2])  # Returns a small sliced top quadrant[cite: 20, 24]

```

---

## 7. The Data Cleaning Engine

Real-world datasets arrive messy—riddled with missing fields, data type collisions, typos, and duplicate rows.

```python
# Handling Missing Values (Theater Seat Reservations)
print(df.isnull().sum())           # Counts total null cells per column[cite: 25]
df['Age'].fillna(30, inplace=True) # (.fillna) Replaces empty spaces with a baseline value[cite: 25]
df.dropna(inplace=True)            # (.dropna) Purges any row containing an empty slot[cite: 25]

# Material Adjustments & Replacement Swaps
df['Age'] = df['Age'].astype(float) # (.astype) Converts an entire column format type[cite: 25]
df['City'].replace({"BPL": "Bhopal", "IND": "Indore"}, inplace=True) # Custom typos maps[cite: 20, 25]

# Erasing Unwanted Records
df.drop(columns="Score", axis=1, inplace=True) # Drops an unwanted structural tracking branch[cite: 25]
df.drop_duplicates(inplace=True)               # Purges exact clone row records[cite: 25]

```

---

## 8. Boolean Indexing & The Logical Bouncer

Filter through a table layout using strict comparison parameters wrapped directly inside the frame selectors `df[...]`.

* **`&` (AND Bouncer):** Demands **both** conditional gate limits evaluate as completely true.


* **`|` (OR Bouncer):** Allows pass-through if **at least one** filter rule matches cleanly.


* **`~` (NOT Bouncer):** Flips truth conditions completely backward.



```python
# Extract students where Age is over 25 AND Score is over 85
filtered_rows = df[(df['Age'] > 25) & (df['Score'] > 85)][cite: 26]

```

### 💬 Streamlining Expressions via `query()`

To skip repetitive bracket notation, pass natural language filter strings directly into `.query()`. Reference variable handles using the `@` symbol.

```python
pass_mark = 85
# High-readability expression engine
print(df.query("Score >= @pass_mark and Age < 35"))[cite: 26]

```

### 🔤 Vectorized Text Actions via `.str`

Clean and evaluate string-heavy columns instantly using element-wise text methods:

```python
df['Name'].str.lower()            # Forces text fields into lowercase sorting formats[cite: 26]
df[df['Name'].str.contains('a')]  # Extracts every name record containing the letter 'a'[cite: 26]
df[df['Name'].str.startswith('D')] # Targets values starting explicitly with 'D'[cite: 26]

```

---

## 9. Descriptive Statistics & Value Frequencies

Extract numeric summaries and analytical weights across variable series with automated calculation hooks.

```python
print(df['Score'].mean())       # Central arithmetic average[cite: 28, 29]
print(df['Score'].median())     # Midpoint divider value[cite: 28, 29]
print(df.std(numeric_only=True)) # Distribution dispersion metric[cite: 28]

# Relationship Maps
print(df.corr(numeric_only=True)) # Calculates mathematical correlation slopes[cite: 28, 29]
print(df.cov(numeric_only=True))  # Explores data variance dependencies[cite: 28, 29]

```

### 📊 Frequency Distribution Tables

Use `value_counts()` on categorical variables to count instances. Set `normalize=True` to print percentages.

```python
# Show city distributions as relative percentage breakdowns
print(df['City'].value_counts(normalize=True) * 100) # Output: Bhopal -> 50%[cite: 29]

```

---

## 10. The Split-Apply-Combine Workflow (`groupby`)

The `.groupby()` tool divides large tables into smart aggregations using a three-tiered summary architecture:

```
  [ Raw Table Data ] ──> Split by "Department" ──> Apply mean() / max() ──> Combine Summary

```

```python
# Question: What is the mean salary and the min/max age profile inside each department?
summary = df.groupby('Department').agg({
    'Salary': ['mean', 'min', 'max'],
    'Age': ['min', 'max']
})
print(summary)

```

---

## 11. Structural Combinations (`concat`, `merge`, & `join`)

When your insights are scattered across different sheets, combine them together using relational joining methods.

* **`pd.concat()` — Stacking Rows or Columns:**
Glues separate DataFrames together vertically (stacking rows with `axis=0`) or horizontally (extending columns side-by-side with `axis=1`).


```python
# Vertical stacking of similar datasets
combined_rows = pd.concat([df1, df2], ignore_index=True)

```


* **`pd.merge()` — SQL-Style Relational Joins:**
Matches tables row-by-row based on a shared key or identity column. Supports multi-relational structures: `inner` (only exact key matches), `left`, `right`, and `outer` (grabs everything, leaving blanks for mismatches).


```python
# Connect product specifications with transactional units sold logs
merged_report = pd.merge(products, sales, on="ProductID", how="inner")

```


* **`DataFrame.join()` — Index-Based Alignments:**
A shortcut method built specifically to merge secondary descriptor columns onto a target DataFrame by directly referencing their row layout indices.



---

## 12. Working with Time Series Data

Pandas treats dates and timelines as native interactive objects rather than standard passive text strings.

* **`pd.to_datetime()` — The Timeline Parser:**
Translates messy text formats, forward slashes, or mixed strings into uniform datetime objects.


```python
# Convert order entries into true standardized datetime fields
df['OrderDate'] = pd.to_datetime(df['OrderDate'], format='mixed', errors='coerce')

```


* **Temporal Resampling (`.resample()`):**
Once a datetime column is promoted as your active tracking index via `.set_index()`, you can instantly bundle up and summarize performance weights into chunks:


* `resample('ME').sum()` groups data into **Month-End** summary totals.


* `resample('W').mean()` flattens chaotic transactional steps into clean **Weekly** rolling averages.





```python
# Switch to a temporal index layout and recalculate weekly trends
df.set_index('VisitDate', inplace=True)
weekly_trends = df.resample('W').mean()

```

---

## 13. Summary

* Pandas provides labeled tabular data frame representations that are much faster and more advanced than standard Python loops.


* Data pipelines scale smoothly: import with parsing hooks, profile parameters using `info()`, scrub missing rows with `fillna()`, and organize layouts sequentially using `sort_values()`.


* Index structures cut cleanly across positional coordinates with `.iloc`, structural labels filter using `.loc`, and relational links slide together seamlessly across `merge()` and `concat()` boundaries.


* Temporal sequences scale seamlessly from text timestamps into active, responsive dashboards using `.to_datetime()` and structural `.resample()` aggregates.



---

## 📂 Homework & Lab Assignment Directory

* `Pandas_Class1.ipynb` / `pandas_class1_assig.ipynb`: Series creations, explicit row keys, list ingestion, and basic data frame mapping.


* `Pandas_Class2.ipynb` / `Pandas_class3.ipynb` / `pandas_2_&_3_Assign_.ipynb`: Profile check workflows, null imputation methods, and column datatype conversions.


* `Pandas_class4.ipynb` / `pandas_class4_assignment.ipynb`: Logical operator filtering blocks, text matching methods, and query strings.


* `Pandas_Class5.ipynb` / `pandas_Class7_Assignment.ipynb`: Value sorting sequences, percentile bounds distributions, and correlation weights.


* `Pandas_class6.ipynb`: Group partitioning loops, aggregation blocks, custom crosstab counters, and spreadsheet summary view tools.


* `Pandas_class7_.ipynb`: Horizontal stacking operations, vertical index binding loops, and custom join type diagnostics.


* `Pandas_class8.ipynb`: Chronological date conversions, datetime formatting properties, and transactional timeline metrics.



```

```
