
---

# 🐼 Pandas - Class 1: Introduction & Setup

Welcome to the structured notes repository for **Pandas Class 1**. This document serves as a comprehensive, beginner-friendly guide covering core multi-dimensional array layouts, fundamental Pandas data structures, data creation pipelines, and localized element selection.

---

## 📋 Table of Contents

1. [What is Pandas and Why Use It?](https://www.google.com/search?q=%231-what-is-pandas-and-why-use-it)
2. [Installing & Importing Pandas](https://www.google.com/search?q=%232-installing--importing-pandas)
3. [Understanding Series vs. DataFrames](https://www.google.com/search?q=%233-understanding-series-vs-dataframes)
4. [Data Structural Setup & Creation](https://www.google.com/search?q=%234-data-structural-setup--creation)
* [Creating a Series](https://www.google.com/search?q=%23a-creating-a-series)
* [Creating a DataFrame (Dictionary Setup)](https://www.google.com/search?q=%23b-creating-a-dataframe-dictionary-setup)
* [Creating a DataFrame (Nested Row Lists)](https://www.google.com/search?q=%23c-creating-a-dataframe-nested-row-lists)
* [Creating a DataFrame (Random NumPy Matrices)](https://www.google.com/search?q=%23d-creating-a-dataframe-random-numpy-matrices)


5. [Data Selection & Slicing (`.loc`)](https://www.google.com/search?q=%235-data-selection--slicing-loc)
6. [External File Parsing (Sneak Peek)](https://www.google.com/search?q=%236-external-file-parsing-sneak-peek)
7. [Summary](https://www.google.com/search?q=%237-summary)

---

## 1. What is Pandas and Why Use It?

**Pandas** is a foundational open-source Python library optimized for fast, flexible, and expressive data analysis and manipulation.

* **Main Structures:** Provides two primary structural archetypes—**Series** (1D) and **DataFrame** (2D).
* **Tabular Simplicity:** Designed to make working with labeled, tabular data seamless and intuitive.
* **Data Processing:** Ideal for structural cleaning, processing transformations, and aggregating raw datasets.
* **Ecosystem Integration:** Works out of the box with core scientific tools like **NumPy**, **Matplotlib**, and **Scikit-Learn**.

---

## 2. Installing & Importing Pandas

To install the package dependency to your localized system workspace environment, run the following terminal script command:

```bash
pip install pandas

```

Once installed, include it within your project source code using the standard community-adopted alias:

```python
import pandas as pd

```

---

## 3. Understanding Series vs. DataFrames

Pandas handles dimensions cleanly by isolating structured attributes:

| Structure | Dimensionality | Description / Analogy |
| --- | --- | --- |
| **Series** | **1D** Array | A single column of data with isolated row indexing (like a column in Excel). |
| **DataFrame** | **2D** Table | A full rectangular grid structured via rows and columns (like a complete spreadsheet). |

---

## 4. Data Structural Setup & Creation

### A. Creating a Series

A Series can be built out of core Python lists while optionally assigning explicit custom indexing keys to rows.

```python
# Instantiating a 1D structural Series with custom player tags
marks = pd.Series(,
                  index=['Ronaldo', 'Messi', 'Virat', 'Dhoni', 'Mbappe'])
print(marks)

```

### B. Creating a DataFrame (Dictionary Setup)

When converting standard Python dictionaries, dictionary **keys** resolve directly as your table column names, while matching list values pack down into matching row items.

```python
# Mapping tracking lists into a standard dictionary schema
info = pd.DataFrame({
    'name': ['Rahul', 'Devraj', 'Abhishek', 'Rishi'],
    'age':,
    'marks':
})
print(info)

```

### C. Creating a DataFrame (Nested Row Lists)

You can construct tabular grids row-by-row by explicitly declaring individual arrays within an outer wrapper list and mapping names via the `columns` parameter.

```python
# Constructing records step-by-step
information = pd.DataFrame([
    ['Rahul', 52, 80],
    ['Devraj', 22, 85],
    ['Abhishek', 60, 55]
], columns=['Name', 'Age', 'Marks'])
print(information)

```

### D. Creating a DataFrame (Random NumPy Matrices)

You can directly bridge multi-dimensional raw arrays generated via **NumPy**'s random distributions into clean DataFrames.

```python
import numpy as np

# Generates a 3x4 array matrix layout with values from 1 to 99
arr = np.random.randint(1, 100, size=(3, 4))

arr_df = pd.DataFrame(arr, columns=['A', 'B', 'C', 'D'])
print(arr_df)

```

---

## 5. Data Selection & Slicing (`.loc`)

Pandas supports targeted data extraction out of structured DataFrames using bracket labels or the `.loc` accessor attribute:

* **Isolate/Slice Single Column:**
```python
info['name']

```


* **Fetch Full Dimensional Row by Index Label:**
```python
info.loc

```


* **Select Matrix Intersect Coordinates (Specific Value):**
```python
# Format: dataframe.loc[row_label, column_name]
info.loc[1, 'name']  # Returns: 'Devraj'

```



---

## 6. External File Parsing (Sneak Peek)

Beyond building datasets programmatically, you can ingest external structured data assets instantly into local variables using built-in high-performance parsing tools:

```python
# Loading standard delimited text arrays
pd.read_csv('file.csv')

# Loading native office spreadsheet workbooks
pd.read_excel('file.xlsx')

```

---

## 7. Summary

* **Pandas** acts  as the industry standard for starting high-octane data preprocessing pipelines.
* Explored basic building block architectures, scaling from **1D Series** arrays up to complex **2D DataFrames**.
* Mastered multiple data synthesis pipelines utilizing native dictionaries, lists, arrays, and NumPy generation workflows.
* Introduced targeting mechanisms to query row records and intersection parameters instantly using `.loc`.
* 
---

## 📂 Assignment_01 File

* `pandas_class1_assig.....ipynb`: The primary Jupyter Notebook containing the problem statements and solution cells.

