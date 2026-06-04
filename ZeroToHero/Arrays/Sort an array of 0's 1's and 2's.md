# Sort an Array of 0's, 1's and 2's 
Problem Link:  [LeetCode 75 - Sort Colors](https://leetcode.com/problems/sort-colors/)

## Problem Statement

Given an array `nums` consisting only of `0`, `1`, and `2`, sort the array in ascending order without using any built-in sorting algorithm.

---

## Example 1

### Input

```text
nums = [1, 0, 2, 1, 0]
```

### Output

```text
[0, 0, 1, 1, 2]
```

### Explanation

The array contains:

- 2 zeroes
- 2 ones
- 1 two

After sorting:

```text
[0, 0, 1, 1, 2]
```

---

## Example 2

### Input

```text
nums = [0, 0, 1, 1, 1]
```

### Output

```text
[0, 0, 1, 1, 1]
```

### Explanation

The array already follows sorted order.

---

# Approach: Dutch National Flag Algorithm

## Idea

Maintain three pointers:

- `l` → Position where the next `0` should be placed.
- `m` → Current element under consideration.
- `r` → Position where the next `2` should be placed.

### Rules

1. If current element is `0`
   - Swap with `l`
   - Move both `l` and `m`

2. If current element is `1`
   - It is already in the correct region
   - Move `m`

3. If current element is `2`
   - Swap with `r`
   - Move `r`
   - Do not move `m` because the swapped element needs to be checked

---

## Code

```python
l, m, r = 0, 0, len(nums) - 1

while m <= r:

    if nums[m] == 1:
        m += 1                      # 1 is already in correct position

    elif nums[m] == 0:
        nums[l], nums[m] = nums[m], nums[l]  # Move 0 to left side
        l += 1
        m += 1

    else:
        nums[r], nums[m] = nums[m], nums[r]  # Move 2 to right side
        r -= 1

return nums
```

---

# Important Lines Explained

### Initialize Three Pointers

```python
l, m, r = 0, 0, len(nums) - 1
```

- `l` tracks the boundary of sorted zeroes.
- `m` scans the array.
- `r` tracks the boundary of sorted twos.

---

### Process Until Middle Crosses Right

```python
while m <= r:
```

Continue processing until all elements are placed in their correct regions.

---

### Handle 1

```python
if nums[m] == 1:
    m += 1
```

- `1` belongs in the middle.
- No swapping needed.

---

### Handle 0

```python
nums[l], nums[m] = nums[m], nums[l]
```

Move the current `0` to the left section.

```python
l += 1
m += 1
```

Expand both the left region and scanning region.

---

### Handle 2

```python
nums[r], nums[m] = nums[m], nums[r]
```

Move the current `2` to the right section.

```python
r -= 1
```

Shrink the right region.

Do **not** increment `m` because the newly swapped value still needs to be checked.

---

# Dry Run

Input:

```text
[1, 0, 2, 1, 0]
```

| l | m | r | Array |
|---|---|---|--------|
| 0 | 0 | 4 | [1,0,2,1,0] |
| 0 | 1 | 4 | [1,0,2,1,0] |
| 1 | 2 | 4 | [0,1,2,1,0] |
| 1 | 2 | 3 | [0,1,0,1,2] |
| 2 | 3 | 3 | [0,0,1,1,2] |
| 2 | 4 | 3 | [0,0,1,1,2] |

Final Output:

```text
[0,0,1,1,2]
```

---

# Complexity Analysis

### Time Complexity

```text
O(n)
```

Each element is processed at most once.

### Space Complexity

```text
O(1)
```

Only three pointers are used.

---

# Key Learning

- Dutch National Flag Algorithm
- Three Pointer Technique
- In-place Sorting
- One-pass Traversal
- Constant Space Optimization

---

# Tags

`Array` `Two Pointers` `Sorting` `Dutch National Flag Algorithm`