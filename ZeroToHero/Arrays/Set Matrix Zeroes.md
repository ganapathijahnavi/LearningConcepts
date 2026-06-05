# Set Matrix Zeroes

## Problem Link

[LeetCode 73 - Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

## Problem Statement

Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`.

You must do it **in-place**.

---

## Example 1

### Input

```text
matrix = [[1,1,1],
          [1,0,1],
          [1,1,1]]
```

### Output

```text
[[1,0,1],
 [0,0,0],
 [1,0,1]]
```

### Explanation

Element at position `(1,1)` is `0`, so its entire row and column are set to `0`.

---

## Example 2

### Input

```text
matrix = [[0,1,2,0],
          [3,4,5,2],
          [1,3,1,5]]
```

### Output

```text
[[0,0,0,0],
 [0,4,5,0],
 [0,3,1,0]]
```

### Explanation

There are two zeroes at positions `(0,0)` and `(0,3)`.

- Row 0 becomes all zeroes.
- Column 0 becomes all zeroes.
- Column 3 becomes all zeroes.

---

# Approach 1: Store Zero Positions

## Idea

- Traverse the matrix and store all positions containing `0`.
- For every stored position:
  - Set its entire row to `0`.
  - Set its entire column to `0`.

## Code

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:

        row, col = len(matrix), len(matrix[0])

        count = []

        for k in range(row * col):

            i = k // col
            j = k % col

            if matrix[i][j] == 0:
                count.append((i, j))  # Store positions of zeroes

        for j in count:

            m, n = j

            for k in range(row):
                matrix[k][n] = 0      # Make entire column zero

            for k in range(col):
                matrix[m][k] = 0      # Make entire row zero

        return matrix
```

## Important Lines Explained

### Store Zero Positions

```python
count.append((i, j))
```

Stores coordinates of every zero found in the matrix.

---

### Convert 1D Index to 2D Coordinates

```python
i = k // col
j = k % col
```

Maps a single loop variable into row and column indices.

---

### Make Entire Column Zero

```python
for k in range(row):
    matrix[k][n] = 0
```

Sets all elements in column `n` to zero.

---

### Make Entire Row Zero

```python
for k in range(col):
    matrix[m][k] = 0
```

Sets all elements in row `m` to zero.

---

## Complexity Analysis

### Time Complexity

```text
O((m*n) + z*(m+n))
```

where `z` is the number of zeroes.

### Space Complexity

```text
O(z)
```

for storing zero positions.

---

# Approach 2: Optimized In-Place Solution

## Idea

Use:

- First row as column markers.
- First column as row markers.

This avoids using extra space.

### Steps

1. Check if first row originally contains a zero.
2. Check if first column originally contains a zero.
3. Use first row and first column as markers.
4. Update matrix based on markers.
5. Finally process first row and first column.

---

## Code

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:

        m, n = len(matrix), len(matrix[0])

        first_row_zero = False
        first_col_zero = False

        # Check first row
        for i in range(n):
            if matrix[0][i] == 0:
                first_row_zero = True
                break

        # Check first column
        for j in range(m):
            if matrix[j][0] == 0:
                first_col_zero = True
                break

        # Mark rows and columns
        for i in range(1, m):
            for j in range(1, n):

                if matrix[i][j] == 0:
                    matrix[0][j] = 0
                    matrix[i][0] = 0

        # Apply markers
        for i in range(1, m):
            for j in range(1, n):

                if matrix[0][j] == 0 or matrix[i][0] == 0:
                    matrix[i][j] = 0

        # Handle first row
        if first_row_zero:
            for i in range(n):
                matrix[0][i] = 0

        # Handle first column
        if first_col_zero:
            for j in range(m):
                matrix[j][0] = 0
```

## Important Lines Explained

### Detect Zero in First Row

```python
if matrix[0][i] == 0:
    first_row_zero = True
```

Stores whether the first row must be zeroed later.

---

### Detect Zero in First Column

```python
if matrix[j][0] == 0:
    first_col_zero = True
```

Stores whether the first column must be zeroed later.

---

### Mark Rows and Columns

```python
matrix[0][j] = 0
matrix[i][0] = 0
```

Instead of using extra arrays, the first row and first column are used as markers.

---

### Apply Markers

```python
if matrix[0][j] == 0 or matrix[i][0] == 0:
    matrix[i][j] = 0
```

If a row or column was marked, set the current cell to zero.

---

### Handle First Row

```python
if first_row_zero:
```

The first row was used as storage, so process it separately.

---

### Handle First Column

```python
if first_col_zero:
```

The first column was used as storage, so process it separately.

---

# Complexity Analysis

### Time Complexity

```text
O(m × n)
```

Single traversal for marking and updating.

### Space Complexity

```text
O(1)
```

No extra data structures are used.

---

# Key Learning

- Matrix Traversal
- In-Place Modification
- Marker Technique
- Space Optimization
- First Row and First Column as Hash Storage

---

# Tags

`Array` `Matrix` `Hashing` `In-Place` `LeetCode 73`