# Linear Search (Without Recursion)

## Problem Link

[Naukri Code360 - Linear Search](https://www.naukri.com/code360/problems/linear-search_6922070)

## Problem Statement

Given an array of integers and a key, find the index of the key using Linear Search.

Return the index if the key is found; otherwise return `-1`.

---

## Example 1

### Input

```text
arr = [10, 20, 30, 40, 50]
key = 30
```

### Output

```text
2
```

### Explanation

The element `30` is present at index `2`.

---

## Example 2

### Input

```text
arr = [10, 20, 30, 40, 50]
key = 60
```

### Output

```text
-1
```

### Explanation

The element `60` is not present in the array.

---

# Approach

## Idea

- Traverse the array from left to right.
- Compare each element with the key.
- If a match is found, return its index.
- If the entire array is traversed and no match is found, return `-1`.

---

## Code

```python
arr = list(map(int, input().split()))
key = int(input())

for i in range(len(arr)):

    if arr[i] == key:     # Element found
        print(i)
        break

else:
    print(-1)             # Element not found
```

---

# Important Lines Explained

### Traverse the Array

```python
for i in range(len(arr)):
```

Iterates through every index of the array.

---

### Check for Match

```python
if arr[i] == key:
```

Compares the current element with the search key.

---

### Return/Print Index

```python
print(i)
```

Outputs the index where the key is found.

---

### Element Not Found

```python
print(-1)
```

Executed only if the key is not present in the array.

---

# Dry Run

Input:

```text
arr = [10, 20, 30, 40, 50]
key = 30
```

| Index | Element | Comparison |
|---------|---------|---------|
| 0 | 10 | 10 != 30 |
| 1 | 20 | 20 != 30 |
| 2 | 30 | 30 == 30 ✓ |

Output:

```text
2
```

---

# Complexity Analysis

### Time Complexity

```text
O(n)
```

In the worst case, every element may need to be checked.

### Space Complexity

```text
O(1)
```

No extra space is used.

---

# Key Learning

- Linear Search Algorithm
- Sequential Traversal
- Searching in Unsorted Arrays
- Basic Iteration Techniques

---

# Tags

`Array` `Searching` `Linear Search`