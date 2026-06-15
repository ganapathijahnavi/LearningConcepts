Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2 as a string.
You must solve the problem without using any built-in library for handling large integers (such as BigInteger). You must also not convert the inputs to integers directly.
Example 1:
Input: num1 = "11", num2 = "123"
Output: "134"

Example 2:
Input: num1 = "456", num2a# Add Strings

## Problem Link

[LeetCode 415 - Add Strings](https://leetcode.com/problems/add-strings/)

## Problem Statement

Given two non-negative integers, `num1` and `num2` represented as strings, return their sum as a string.

You must solve the problem without:

- Using any built-in library for handling large integers.
- Converting the input strings directly into integers.

---

## Example 1

### Input

```text
num1 = "11"
num2 = "123"
```

### Output

```text
"134"
```

---

## Example 2

### Input

```text
num1 = "456"
num2 = "77"
```

### Output

```text
"533"
```

---

## Example 3

### Input

```text
num1 = "0"
num2 = "0"
```

### Output

```text
"0"
```

---

# Approach

## Idea

Simulate elementary school addition.

- Start from the last digit of both strings.
- Add corresponding digits along with the carry.
- Store the current digit in the result.
- Update the carry.
- Continue until all digits are processed.
- Reverse the result at the end.

---

## Code

```python
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:

        l, r = len(num1) - 1, len(num2) - 1
        carr = 0
        res = []

        while l >= 0 or r >= 0:

            if l >= 0:
                a = int(num1[l])
            else:
                a = 0

            if r >= 0:
                b = int(num2[r])
            else:
                b = 0

            tot = a + b + carr

            res.append(str(tot % 10))  # Current digit
            carr = tot // 10           # Carry for next step

            l -= 1
            r -= 1

        if carr:
            res.append(str(carr))

        result_str = "".join(reversed(res))

        return result_str.lstrip('0') or "0"
```

---

# Important Lines Explained

### Start From Last Digits

```python
l, r = len(num1) - 1, len(num2) - 1
```

Addition starts from the least significant digit (rightmost digit).

---

### Store Carry

```python
carr = 0
```

Stores the carry generated during addition.

---

### Continue Until All Digits Are Processed

```python
while l >= 0 or r >= 0:
```

Continue processing until both strings are fully traversed.

---

### Handle Different Length Strings

```python
a = int(num1[l]) if l >= 0 else 0
b = int(num2[r]) if r >= 0 else 0
```

If one string is shorter, treat missing digits as `0`.

---

### Calculate Current Sum

```python
tot = a + b + carr
```

Add:

- Current digit from `num1`
- Current digit from `num2`
- Previous carry

---

### Store Current Digit

```python
res.append(str(tot % 10))
```

The last digit of the sum becomes part of the answer.

Example:

```text
17 % 10 = 7
```

---

### Update Carry

```python
carr = tot // 10
```

The carry is passed to the next iteration.

Example:

```text
17 // 10 = 1
```

---

### Handle Remaining Carry

```python
if carr:
    res.append(str(carr))
```

If a carry remains after processing all digits, append it.

Example:

```text
999 + 1 = 1000
```

---

### Reverse Result

```python
result_str = "".join(reversed(res))
```

Digits were collected from right to left, so reverse them.

---

### Remove Leading Zeroes

```python
return result_str.lstrip('0') or "0"
```

Removes any leading zeroes while ensuring `"0"` is returned when the result is zero.

---

# Dry Run

Input:

```text
num1 = "456"
num2 = "77"
```

| a | b | Carry In | Total | Digit | Carry Out |
|---|---|---|---|---|---|
| 6 | 7 | 0 | 13 | 3 | 1 |
| 5 | 7 | 1 | 13 | 3 | 1 |
| 4 | 0 | 1 | 5 | 5 | 0 |

Result Array:

```text
["3", "3", "5"]
```

After Reversing:

```text
"533"
```

---

# Complexity Analysis

### Time Complexity

```text
O(max(n, m))
```

Where:

- `n` = length of `num1`
- `m` = length of `num2`

---

### Space Complexity

```text
O(max(n, m))
```

For storing the result string.

---

# Key Learning

- String Traversal
- Simulation of Manual Addition
- Carry Propagation
- Two Pointer Technique
- Handling Large Numbers Without Conversion

---

# Tags

`String` `Math` `Simulation` `Two Pointers` `LeetCode 415` = "77"
Output: "533"

Example 3:
Input: num1 = "0", num2 = "0"
Output: "0"

Code:
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
        l, r = len(num1) - 1, len(num2) - 1
        carr = 0
        res = []
        while l >= 0 or r >= 0 :
            if l >= 0:
                a = int(num1[l])
            else:
                a = 0
            if r >= 0:
                b = int(num2[r])
            else:
                b = 0
            tot = a + b + carr
            res.append(str(tot%10))
            carr = tot // 10 
            l -= 1
            r -= 1
        if carr:
            res.append(str(carr))
        result_str = "".join(reversed(res))
        return result_str.lstrip('0') or "0"
