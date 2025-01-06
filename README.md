# **Data Cleaning Repository**

This repository offers key tools and methods for efficient data cleaning, focusing on handling missing values, duplicates, and inconsistencies. It includes ready-to-use scripts and best practices to enhance data quality and streamline preprocessing workflows.

---

## **What is a Flat File?**

A **flat file** is a simple data storage format that stores data in plain text or binary form. It typically contains records without structured relationships between them, and the records are usually separated by a specific character such as:  

- **Comma (CSV - Comma-Separated Values)**  
- **Tab (TSV - Tab-Separated Values)**  
- **Newline (`\n`)** for separating records  

Flat files are lightweight, portable, and commonly used for data exchange, logs, or simple datasets. However, they lack the complexity and relational structures of databases.

---

## **Reading Flat Files Using `numpy.loadtxt()`**

The `numpy.loadtxt()` function is used to read data from flat files (like `.txt` and `.csv`) and load it into a NumPy array.

### **Syntax:**
```python
numpy.loadtxt(fname, dtype=float, delimiter=None, skiprows=0, usecols=None)
```

### **Key Parameters:**
- **`fname`**: File name or path.
- **`dtype`**: Data type (default is `float`).
- **`delimiter`**: Character used to separate values (e.g., `,`, `\t`).
- **`skiprows`**: Number of rows to skip at the start (e.g., headers).
- **`usecols`**: Specifies which columns to read.

---

### **Example 1: Basic Usage**

**File (`data.txt`):**
```
1.0 2.0 3.0
4.0 5.0 6.0
7.0 8.0 9.0
```

**Code:**
```python
import numpy as np

# Load the file into a NumPy array
data = np.loadtxt('data.txt')
print(data)
```

**Output:**
```
[[1. 2. 3.]
 [4. 5. 6.]
 [7. 8. 9.]]
```

---

### **Example 2: Skipping Rows and Selecting Columns**

**File (`scores.txt`):**
```
# Student Scores
Name  Math  Science  History
John  78    88       92
Alice 82    79       85
Bob   90    92       88
```

**Code:**
```python
import numpy as np

# Load only columns 1 (Math) and 2 (Science), skipping the first two rows
scores = np.loadtxt('scores.txt', skiprows=2, usecols=(1, 2), delimiter=' ')
print(scores)
```

**Output:**
```
[[78. 88.]
 [82. 79.]
 [90. 92.]]
```

---

### **Notes:**
- Use `skiprows` to ignore non-numeric header rows.
- If your file contains both text and numbers, consider using `numpy.genfromtxt()` or `pandas.read_csv()` instead.

---
