# NumPy Learning Guide: Numerical Computing Fundamentals

## Overview
This notebook covers NumPy library from basics to advanced numerical computing. NumPy is the foundation for scientific computing in Python.

**What is NumPy?**
- Python library for numerical and scientific computing
- Provides N-dimensional arrays (ndarrays)
- Fast and memory-efficient operations
- Mathematical and statistical functions
- Foundation for Pandas, Scikit-learn, and other libraries

---

# Part 1: Installation and Setup

## Installation
```bash
pip install numpy
```

## Import NumPy
```python
import numpy as np
```

```python
# Import NumPy
import numpy as np

# Display version
print(f"NumPy version: {np.__version__}")
print(f"NumPy configuration:\n{np.show_config()}")
```

# Part 2: NumPy Arrays

## What is an ndarray?
- N-dimensional array object (the core of NumPy)
- Fixed-size, homogeneous data type
- Efficient storage and computation
- Much faster than Python lists

## Key Attributes
- `shape`: Dimensions of array
- `dtype`: Data type of elements
- `ndim`: Number of dimensions
- `size`: Total number of elements
- `itemsize`: Size of each element in bytes
- `nbytes`: Total size in bytes

```python
# Example: Creating NumPy arrays

# From Python list
arr1 = np.array([1, 2, 3, 4, 5])
print("1D array from list:")
print(arr1)
print(f"Type: {type(arr1)}")

# 2D array
arr2 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print("\n2D array:")
print(arr2)

# 3D array
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print("\n3D array:")
print(arr3)
```

```python
# Example: Array attributes

arr = np.array([[1, 2, 3], [4, 5, 6]])

print(f"Shape: {arr.shape}")
print(f"Data type: {arr.dtype}")
print(f"Number of dimensions: {arr.ndim}")
print(f"Total elements: {arr.size}")
print(f"Bytes per element: {arr.itemsize}")
print(f"Total bytes: {arr.nbytes}")

# Different data types
arr_int = np.array([1, 2, 3], dtype=int)
arr_float = np.array([1, 2, 3], dtype=float)
arr_complex = np.array([1, 2, 3], dtype=complex)
arr_bool = np.array([True, False, True], dtype=bool)

print(f"\nInt dtype: {arr_int.dtype}")
print(f"Float dtype: {arr_float.dtype}")
print(f"Complex dtype: {arr_complex.dtype}")
print(f"Bool dtype: {arr_bool.dtype}")
```

# Part 3: Array Creation Methods

## Common Creation Functions
- `np.zeros()`: Array of zeros
- `np.ones()`: Array of ones
- `np.arange()`: Range of values
- `np.linspace()`: Evenly spaced values
- `np.eye()`: Identity matrix
- `np.random.random()`: Random values
- `np.full()`: Array filled with value

```python
# Example: Array creation methods

# Zeros
zeros = np.zeros((3, 4))
print("Zeros (3x4):")
print(zeros)

# Ones
ones = np.ones((2, 3), dtype=int)
print("\nOnes (2x3):")
print(ones)

# Range
range_arr = np.arange(0, 10, 2)
print(f"\nRange (0 to 10, step 2): {range_arr}")

# Linspace (evenly spaced)
linspace_arr = np.linspace(0, 10, 5)
print(f"Linspace (0 to 10, 5 points): {linspace_arr}")

# Identity matrix
identity = np.eye(3)
print("\nIdentity matrix (3x3):")
print(identity)

# Full (filled with value)
full_arr = np.full((2, 3), 7)
print("\nFull array (2x3) filled with 7:")
print(full_arr)
```

```python
# Example: Random arrays

# Random values between 0 and 1
random_arr = np.random.random((2, 3))
print("Random (0-1):")
print(random_arr)

# Random integers
random_int = np.random.randint(0, 100, (3, 4))
print("\nRandom integers (0-100):")
print(random_int)

# Normal distribution
normal_arr = np.random.normal(0, 1, (2, 3))
print("\nNormal distribution (mean=0, std=1):")
print(normal_arr)
```

# Part 4: Indexing and Slicing

## 1D Indexing
- Similar to Python lists
- Positive and negative indices
- Slicing with [start:stop:step]

## Multi-dimensional Indexing
- Multiple indices: `arr[row, col]`
- Boolean indexing: Filter by condition
- Fancy indexing: Array of indices

```python
# Example: 1D indexing and slicing

arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90])

# Indexing
print(f"First element: {arr[0]}")
print(f"Last element: {arr[-1]}")
print(f"Element at index 3: {arr[3]}")

# Slicing
print(f"\nSlice [2:5]: {arr[2:5]}")
print(f"Slice [::2] (every 2nd): {arr[::2]}")
print(f"Slice [::-1] (reversed): {arr[::-1]}")
print(f"Slice [1:7:2]: {arr[1:7:2]}")
```

```python
# Example: 2D indexing and slicing

arr2d = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
    [13, 14, 15, 16]
])

print("2D Array:")
print(arr2d)

# Element access
print(f"\nElement at [0, 0]: {arr2d[0, 0]}")
print(f"Element at [2, 3]: {arr2d[2, 3]}")

# Row access
print(f"\nRow 1: {arr2d[1]}")

# Column access
print(f"Column 2: {arr2d[:, 2]}")

# Slicing
print(f"\nSlice [1:3, 1:3]:\n{arr2d[1:3, 1:3]}")
print(f"\nSlice [::2, ::2]:\n{arr2d[::2, ::2]}")
```

```python
# Example: Boolean indexing

arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90])

# Filter elements > 40
mask = arr > 40
print(f"Boolean mask (arr > 40): {mask}")
print(f"Elements > 40: {arr[mask]}")

# Multiple conditions
mask2 = (arr > 20) & (arr < 80)
print(f"\nElements between 20 and 80: {arr[mask2]}")

# Using np.where
result = np.where(arr > 50, "High", "Low")
print(f"\nUsing where (> 50): {result}")
```

```python
# Example: Fancy indexing

arr = np.array([10, 20, 30, 40, 50, 60, 70, 80, 90])

# Index array
indices = np.array([0, 2, 4, 8])
print(f"Array: {arr}")
print(f"Indices: {indices}")
print(f"Elements at indices: {arr[indices]}")

# 2D fancy indexing
arr2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
rows = np.array([0, 2])
cols = np.array([0, 2])
print(f"\n2D Array:\n{arr2d}")
print(f"Elements at [0,0] and [2,2]: {arr2d[rows, cols]}")
```

# Part 5: Array Operations

## Element-wise Operations
- Addition, subtraction, multiplication, division
- Power, modulo, floor division
- Comparison operations

## Broadcasting
- Operating on arrays of different shapes
- Automatic expansion of smaller arrays
- Follows specific rules

```python
# Example: Element-wise operations

a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])

print(f"Array a: {a}")
print(f"Array b: {b}")

# Arithmetic operations
print(f"\na + b: {a + b}")
print(f"a - b: {a - b}")
print(f"a * b: {a * b}")
print(f"b / a: {b / a}")
print(f"b ** 2: {b ** 2}")
print(f"b % 3: {b % 3}")

# Operations with scalar
print(f"\na + 10: {a + 10}")
print(f"a * 2: {a * 2}")
print(f"10 / a: {10 / a}")
```

```python
# Example: Comparison operations

a = np.array([1, 2, 3, 4, 5])
b = np.array([2, 2, 2, 4, 6])

print(f"Array a: {a}")
print(f"Array b: {b}")

# Comparisons
print(f"\na == b: {a == b}")
print(f"a < b: {a < b}")
print(f"a > b: {a > b}")
print(f"a <= b: {a <= b}")

# Logical operations
print(f"\n(a < 3) & (b > 2): {(a < 3) & (b > 2)}")
print(f"(a < 3) | (b > 4): {(a < 3) | (b > 4)}")
print(f"~(a < 3): {~(a < 3)}")
```

```python
# Example: Broadcasting

# 1D + scalar
arr1d = np.array([1, 2, 3])
scalar = 10
print(f"1D array + scalar: {arr1d + scalar}")

# Different shapes
arr_3x1 = np.array([[1], [2], [3]])  # Shape (3, 1)
arr_1x3 = np.array([[1, 2, 3]])      # Shape (1, 3)

print(f"\nArray (3,1):\n{arr_3x1}")
print(f"Array (1,3):\n{arr_1x3}")
print(f"Sum (broadcasting to 3x3):\n{arr_3x1 + arr_1x3}")

# 2D + 1D
arr2d = np.array([[1, 2, 3], [4, 5, 6]])
arr1d = np.array([10, 20, 30])
print(f"\n2D array:\n{arr2d}")
print(f"1D array: {arr1d}")
print(f"2D + 1D:\n{arr2d + arr1d}")
```

# Part 6: Mathematical Functions

## Universal Functions (ufuncs)
- `np.sqrt()`: Square root
- `np.exp()`, `np.log()`: Exponential and logarithm
- `np.sin()`, `np.cos()`, `np.tan()`: Trigonometric
- `np.abs()`: Absolute value
- `np.round()`: Rounding

## Array Functions
- `np.sum()`, `np.prod()`: Sum and product
- `np.min()`, `np.max()`: Minimum and maximum
- `np.mean()`, `np.median()`: Mean and median
- `np.std()`, `np.var()`: Standard deviation and variance

```python
# Example: Mathematical functions

arr = np.array([1, 4, 9, 16, 25])

print(f"Array: {arr}")
print(f"\nSquare root: {np.sqrt(arr)}")
print(f"Absolute value: {np.abs(-arr)}")
print(f"Exponential: {np.exp(arr)}")
print(f"Natural log: {np.log(arr)}")
print(f"Log base 10: {np.log10(arr)}")

# Rounding
arr_float = np.array([1.234, 2.567, 3.891, 4.123])
print(f"\nFloat array: {arr_float}")
print(f"Round: {np.round(arr_float)}")
print(f"Round to 2 decimals: {np.round(arr_float, 2)}")
print(f"Floor: {np.floor(arr_float)}")
print(f"Ceil: {np.ceil(arr_float)}")
```

```python
# Example: Trigonometric functions

angles = np.array([0, np.pi/6, np.pi/4, np.pi/3, np.pi/2])

print("Angles (in radians):", angles)
print(f"Sin: {np.sin(angles)}")
print(f"Cos: {np.cos(angles)}")
print(f"Tan: {np.tan(angles)}")

# Inverse
print(f"\nArcsin(0.5): {np.arcsin(0.5)}")
print(f"Arccos(0.5): {np.arccos(0.5)}")
print(f"Arctan(1): {np.arctan(1)}")
```

# Part 7: Statistical Functions

## Descriptive Statistics
- `np.mean()`: Average
- `np.median()`: Median
- `np.std()`: Standard deviation
- `np.var()`: Variance
- `np.min()`, `np.max()`: Minimum, maximum
- `np.percentile()`: Percentiles

## Along Axes
- `axis=0`: Along rows (down)
- `axis=1`: Along columns (across)
- `axis=None`: Entire array

```python
# Example: Statistical functions

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

print(f"Array: {arr}")
print(f"Mean: {np.mean(arr)}")
print(f"Median: {np.median(arr)}")
print(f"Std Dev: {np.std(arr)}")
print(f"Variance: {np.var(arr)}")
print(f"Min: {np.min(arr)}")
print(f"Max: {np.max(arr)}")
print(f"Range: {np.ptp(arr)}")

# Percentiles
print(f"\n25th percentile: {np.percentile(arr, 25)}")
print(f"50th percentile: {np.percentile(arr, 50)}")
print(f"75th percentile: {np.percentile(arr, 75)}")

# Quartiles
print(f"\nQuartiles: {np.percentile(arr, [25, 50, 75])}")
```

```python
# Example: Statistics along axes

arr2d = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

print("2D Array:")
print(arr2d)

# Along entire array
print(f"\nMean (all): {np.mean(arr2d)}")

# Along axis 0 (rows, vertical)
print(f"Mean along axis 0 (columns): {np.mean(arr2d, axis=0)}")

# Along axis 1 (columns, horizontal)
print(f"Mean along axis 1 (rows): {np.mean(arr2d, axis=1)}")

# Sum along axes
print(f"\nSum along axis 0: {np.sum(arr2d, axis=0)}")
print(f"Sum along axis 1: {np.sum(arr2d, axis=1)}")
```

# Part 8: Array Manipulation

## Reshaping
- `reshape()`: Change shape
- `flatten()`: Convert to 1D
- `ravel()`: 1D view (doesn't copy)

## Transposing
- `transpose()`: Transpose array
- `.T`: Shorthand for transpose

## Stacking
- `np.vstack()`: Vertical stack
- `np.hstack()`: Horizontal stack
- `np.dstack()`: Depth stack
- `np.concatenate()`: General concatenate

## Splitting
- `np.split()`: Split array
- `np.hsplit()`: Horizontal split
- `np.vsplit()`: Vertical split

```python
# Example: Reshaping

arr = np.arange(12)
print(f"Original (1D, shape {arr.shape}): {arr}")

# Reshape to 3x4
reshaped = arr.reshape(3, 4)
print(f"\nReshaped to (3, 4):\n{reshaped}")

# Reshape to 2x2x3
reshaped3d = arr.reshape(2, 2, 3)
print(f"\nReshaped to (2, 2, 3):\n{reshaped3d}")

# Flatten
flattened = reshaped.flatten()
print(f"\nFlattened: {flattened}")

# Ravel (view, doesn't copy)
raveled = reshaped.ravel()
print(f"Raveled: {raveled}")
```

```python
# Example: Transpose

arr = np.array([[1, 2, 3], [4, 5, 6]])
print(f"Original (2x3):\n{arr}")

# Transpose
transposed = arr.transpose()
print(f"\nTransposed (3x2):\n{transposed}")

# Using .T shorthand
print(f"\nUsing .T:\n{arr.T}")
```

```python
# Example: Stacking arrays

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(f"Array a: {a}")
print(f"Array b: {b}")

# Vertical stack (row-wise)
vstacked = np.vstack([a, b])
print(f"\nVstack:\n{vstacked}")

# Horizontal stack (column-wise)
hstacked = np.hstack([a, b])
print(f"\nHstack: {hstacked}")

# 2D arrays
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

print(f"\nArray 1:\n{arr1}")
print(f"Array 2:\n{arr2}")
print(f"Vstack:\n{np.vstack([arr1, arr2])}")
print(f"Hstack:\n{np.hstack([arr1, arr2])}")
```

```python
# Example: Splitting arrays

arr = np.arange(12).reshape(3, 4)
print(f"Original array:\n{arr}")

# Horizontal split (into 2 parts)
left, right = np.hsplit(arr, 2)
print(f"\nHorizontal split:")
print(f"Left:\n{left}")
print(f"Right:\n{right}")

# Vertical split
top, bottom = np.vsplit(arr, [2])
print(f"\nVertical split at row 2:")
print(f"Top:\n{top}")
print(f"Bottom:\n{bottom}")
```

# Part 9: Linear Algebra

## Basic Operations
- `np.dot()`: Dot product / matrix multiplication
- `@`: Matrix multiplication operator
- `np.linalg.inv()`: Matrix inverse
- `np.linalg.det()`: Determinant
- `np.linalg.norm()`: Matrix norm
- `np.linalg.eig()`: Eigenvalues and eigenvectors

```python
# Example: Dot product and matrix multiplication

# Vectors
v1 = np.array([1, 2, 3])
v2 = np.array([4, 5, 6])

dot_product = np.dot(v1, v2)
print(f"Vector v1: {v1}")
print(f"Vector v2: {v2}")
print(f"Dot product: {dot_product}")

# Matrices
m1 = np.array([[1, 2], [3, 4]])
m2 = np.array([[5, 6], [7, 8]])

print(f"\nMatrix m1:\n{m1}")
print(f"Matrix m2:\n{m2}")

# Matrix multiplication
mult = np.dot(m1, m2)
print(f"\nm1 · m2 (np.dot):\n{mult}")

# Using @ operator
mult2 = m1 @ m2
print(f"\nm1 @ m2:\n{mult2}")
```

```python
# Example: Matrix operations

m = np.array([[1, 2], [3, 4]])

print(f"Matrix:\n{m}")

# Determinant
det = np.linalg.det(m)
print(f"\nDeterminant: {det}")

# Inverse
inv = np.linalg.inv(m)
print(f"\nInverse:\n{inv}")

# Verify: m · m^-1 = I
print(f"\nm · m^-1:\n{m @ inv}")

# Transpose
print(f"\nTranspose:\n{m.T}")

# Trace (sum of diagonal)
trace = np.trace(m)
print(f"Trace: {trace}")
```

# Part 10: Random Number Generation

## Random Functions
- `np.random.random()`: Uniform [0, 1)
- `np.random.randint()`: Random integers
- `np.random.normal()`: Normal distribution
- `np.random.binomial()`: Binomial distribution
- `np.random.choice()`: Random choice from array
- `np.random.shuffle()`: Shuffle array in place
- `np.random.permutation()`: Random permutation

```python
# Example: Random number generation

# Set seed for reproducibility
np.random.seed(42)

# Uniform distribution [0, 1)
uniform = np.random.random(5)
print(f"Uniform [0,1): {uniform}")

# Random integers
integers = np.random.randint(1, 100, 10)
print(f"\nRandom integers (1-100): {integers}")

# Normal distribution
normal = np.random.normal(0, 1, 5)
print(f"\nNormal (mean=0, std=1): {normal}")

# Binomial distribution
binomial = np.random.binomial(n=10, p=0.5, size=5)
print(f"\nBinomial (n=10, p=0.5): {binomial}")

# Random choice
choices = np.random.choice(['red', 'green', 'blue'], 5)
print(f"\nRandom choice: {choices}")
```

```python
# Example: Shuffle and permutation

arr = np.arange(10)
print(f"Original: {arr}")

# Shuffle (modifies in place)
arr_copy = arr.copy()
np.random.shuffle(arr_copy)
print(f"Shuffled: {arr_copy}")

# Permutation (returns new array)
perm = np.random.permutation(arr)
print(f"Permutation: {perm}")
print(f"Original unchanged: {arr}")
```

# Part 11: Practice Exercises

## Exercise 1: Array Statistics
Calculate statistics on an array.

```python
# Exercise 1: Array Statistics

# Generate random data
np.random.seed(42)
data = np.random.normal(100, 15, 100)

print(f"Data shape: {data.shape}")
print(f"Mean: {np.mean(data):.2f}")
print(f"Median: {np.median(data):.2f}")
print(f"Std Dev: {np.std(data):.2f}")
print(f"Min: {np.min(data):.2f}")
print(f"Max: {np.max(data):.2f}")
print(f"Q1 (25%): {np.percentile(data, 25):.2f}")
print(f"Q3 (75%): {np.percentile(data, 75):.2f}")

# Count values in range
in_range = np.sum((data > 85) & (data < 115))
percentage = (in_range / len(data)) * 100
print(f"\nValues between 85-115: {in_range} ({percentage:.1f}%)")
```

## Exercise 2: Matrix Operations
Perform matrix operations.

```python
# Exercise 2: Matrix Operations

# Create matrices
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

print(f"Matrix A:\n{A}")
print(f"\nMatrix B:\n{B}")

# Element-wise operations
print(f"\nA + B:\n{A + B}")
print(f"A * B (element-wise):\n{A * B}")

# Matrix multiplication
print(f"\nA @ B (matrix mult):\n{A @ B}")

# Transpose
print(f"\nA.T:\n{A.T}")

# Determinant and inverse
print(f"\nDet(A): {np.linalg.det(A):.2f}")
print(f"A^-1:\n{np.linalg.inv(A).round(2)}")
```

## Exercise 3: Array Filtering
Filter array elements based on conditions.

```python
# Exercise 3: Array Filtering

# Generate data
ages = np.array([18, 25, 30, 45, 52, 28, 35, 60, 22, 48])
salaries = np.array([30000, 45000, 55000, 80000, 90000, 50000, 65000, 100000, 35000, 85000])

print("Data:")
print(f"Ages: {ages}")
print(f"Salaries: {salaries}")

# Filter: age > 30 and salary > 50000
mask = (ages > 30) & (salaries > 50000)
filtered_ages = ages[mask]
filtered_salaries = salaries[mask]

print(f"\nFiltered (age > 30 and salary > 50000):")
print(f"Ages: {filtered_ages}")
print(f"Salaries: {filtered_salaries}")

# Statistics for filtered data
print(f"\nAverage age: {np.mean(filtered_ages):.1f}")
print(f"Average salary: ${np.mean(filtered_salaries):.0f}")
```

## Exercise 4: Data Normalization
Normalize array data.

```python
# Exercise 4: Data Normalization

# Generate data
np.random.seed(42)
data = np.random.normal(100, 20, 10)

print(f"Original data: {np.round(data, 2)}")
print(f"Mean: {np.mean(data):.2f}")
print(f"Std Dev: {np.std(data):.2f}")

# Min-Max normalization [0, 1]
min_max_norm = (data - np.min(data)) / (np.max(data) - np.min(data))
print(f"\nMin-Max normalized: {np.round(min_max_norm, 3)}")
print(f"Range: [{np.min(min_max_norm)}, {np.max(min_max_norm)}]")

# Z-score normalization
z_norm = (data - np.mean(data)) / np.std(data)
print(f"\nZ-score normalized: {np.round(z_norm, 3)}")
print(f"Mean: {np.mean(z_norm):.6f}")
print(f"Std Dev: {np.std(z_norm):.2f}")
```

## Exercise 5: 2D Array Manipulation
Work with 2D arrays.

```python
# Exercise 5: 2D Array Manipulation

# Create 2D data (like a spreadsheet)
data_2d = np.array([
    [85, 90, 88],  # Student 1 scores
    [92, 88, 95],  # Student 2 scores
    [78, 82, 80],  # Student 3 scores
    [95, 92, 98]   # Student 4 scores
])

print("Student scores (rows=students, cols=exams):")
print(data_2d)

# Average by student (row-wise)
student_avg = np.mean(data_2d, axis=1)
print(f"\nAverage score per student: {np.round(student_avg, 2)}")

# Average by exam (column-wise)
exam_avg = np.mean(data_2d, axis=0)
print(f"Average score per exam: {np.round(exam_avg, 2)}")

# Best and worst performers
best_student = np.argmax(student_avg)
worst_student = np.argmin(student_avg)
print(f"\nBest student: Student {best_student + 1} ({student_avg[best_student]:.2f})")
print(f"Worst student: Student {worst_student + 1} ({student_avg[worst_student]:.2f})")
```

# Key NumPy Concepts Summary

## Core Concepts
1. **ndarray**: N-dimensional array (core data structure)
2. **Broadcasting**: Operating on arrays of different shapes
3. **Vectorization**: Use operations on whole arrays instead of loops
4. **Universal Functions (ufuncs)**: Element-wise operations
5. **Axes**: Dimensions for operations (axis=0 rows, axis=1 columns)

## Common Operations
| Task | Function | Example |
|------|----------|----------|
| Create array | `np.array()` | Create from list |
| Shape | `shape`, `reshape()` | Get/change dimensions |
| Access | `indexing`, `slicing` | Get elements |
| Compute | `ufuncs` | Element-wise math |
| Aggregate | `sum()`, `mean()` | Combine values |
| Filter | `boolean indexing` | Select by condition |
| Stack | `vstack()`, `hstack()` | Combine arrays |
| Linear Algebra | `dot()`, `linalg` | Matrix operations |

## Performance Tips
- Use NumPy operations instead of Python loops
- Broadcasting avoids creating large temporary arrays
- Use `dtype` efficiently (int32 vs int64)
- Use views when possible to save memory
- Pre-allocate arrays when size is known

## Comparison: NumPy vs Python
- NumPy: 50-100x faster for numerical operations
- NumPy: More memory efficient
- NumPy: Better for vectorized operations
- Python lists: Better for heterogeneous data

---

**Happy Numerical Computing! 🔢**
