# Add Binary

## Problem Link

[LeetCode 67 - Add Binary](https://leetcode.com/problems/add-binary/)

## Problem Statement

Given two binary strings `a` and `b`, return their sum as a binary string.

---

## Example 1

### Input

```text
a = "11"
b = "1"
```

### Output

```text
"100"
```

### Explanation

```text
  11  (3)
+  1  (1)
----
 100  (4)
```

---

## Example 2

### Input

```text
a = "1010"
b = "1011"
```

### Output

```text
"10101"
```

### Explanation

```text
  1010  (10)
+ 1011  (11)
------
 10101  (21)
```

---

# Approach

## Idea

Simulate the way we perform addition manually.

- Start from the rightmost digit of both strings.
- Add corresponding bits along with the carry.
- Store the result bit.
- Update the carry.
- Continue until all digits and carry are processed.

---

## Code

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:

        i, j = len(a) - 1, len(b) - 1
        carry = 0
        res = []

        while i >= 0 or j >= 0 or carry:

            x = int(a[i]) if i >= 0 else 0
            y = int(b[j]) if j >= 0 else 0

            total = x + y + carry

            res.append(str(total % 2))  # Current binary digit
            carry = total // 2          # Carry for next iteration

            i -= 1
            j -= 1

        return "".join(reversed(res))
```

---

# Important Lines Explained

### Start From Last Digit

```python
i, j = len(a) - 1, len(b) - 1
```

Binary addition starts from the least significant bit (rightmost digit).

---

### Continue Until All Digits and Carry Are Processed

```python
while i >= 0 or j >= 0 or carry:
```

The loop continues as long as:

- There are digits remaining in `a`
- There are digits remaining in `b`
- There is a carry left

---

### Handle Different Length Strings

```python
x = int(a[i]) if i >= 0 else 0
y = int(b[j]) if j >= 0 else 0
```

If one string is shorter, use `0` as the missing bit.

---

### Calculate Sum

```python
total = x + y + carry
```

Add:

- Current bit from `a`
- Current bit from `b`
- Previous carry

---

### Store Result Bit

```python
res.append(str(total % 2))
```

The remainder after dividing by `2` gives the current binary digit.

Examples:

```text
Total = 3 → 3 % 2 = 1
Total = 2 → 2 % 2 = 0
Total = 1 → 1 % 2 = 1
```

---

### Update Carry

```python
carry = total // 2
```

Examples:

```text
3 // 2 = 1
2 // 2 = 1
1 // 2 = 0
```

---

### Reverse Result

```python
return "".join(reversed(res))
```

Digits are generated from right to left, so reverse them before returning.

---

# Dry Run

Input:

```text
a = "11"
b = "1"
```

| x | y | Carry In | Total | Result Bit | Carry Out |
|---|---|---|---|---|---|
| 1 | 1 | 0 | 2 | 0 | 1 |
| 1 | 0 | 1 | 2 | 0 | 1 |
| 0 | 0 | 1 | 1 | 1 | 0 |

Result Array:

```text
["0", "0", "1"]
```

After Reversing:

```text
"100"
```

---

# Complexity Analysis

### Time Complexity

```text
O(max(n, m))
```

Where:

- `n` = length of string `a`
- `m` = length of string `b`

---

### Space Complexity

```text
O(max(n, m))
```

For storing the result.

---

# Key Learning

- Binary Arithmetic
- Carry Handling
- String Traversal from Right to Left
- Simulation Technique
- Two Pointer Approach

---

# Tags

`String` `Math` `Binary` `Simulation` `LeetCode 67`