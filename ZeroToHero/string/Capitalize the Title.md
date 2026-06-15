# Capitalize the Title

## Problem Link

[LeetCode 2129 - Capitalize the Title](https://leetcode.com/problems/capitalize-the-title/)

## Problem Statement

You are given a string `title` consisting of one or more words separated by a single space.

Capitalize each word according to the following rules:

- If the word length is `1` or `2`, convert all letters to lowercase.
- Otherwise, capitalize the first letter and convert the remaining letters to lowercase.

Return the capitalized title.

---

## Example 1

### Input

```text
title = "capiTalIze tHe titLe"
```

### Output

```text
"Capitalize The Title"
```

### Explanation

All words have length greater than 2.

Therefore:

- First letter → Uppercase
- Remaining letters → Lowercase

---

## Example 2

### Input

```text
title = "First leTTeR of EACH Word"
```

### Output

```text
"First Letter of Each Word"
```

### Explanation

The word `"of"` has length `2`, so it becomes lowercase.

All other words have length greater than `2`.

---

## Example 3

### Input

```text
title = "i lOve leetcode"
```

### Output

```text
"i Love Leetcode"
```

### Explanation

The word `"i"` has length `1`, so it remains lowercase.

The remaining words follow title capitalization rules.

---

# Approach

## Idea

1. Split the string into individual words.
2. Traverse each word.
3. If the word length is less than or equal to `2`, convert it to lowercase.
4. Otherwise, capitalize the first letter and convert the remaining letters to lowercase.
5. Join all processed words back into a single string.

---

## Code

```python
class Solution:
    def capitalizeTitle(self, title: str) -> str:

        tit = list(title.split(" "))
        res = []

        for i in tit:

            if len(i) <= 2:
                res.append(i.lower())      # Entire word lowercase

            else:
                res.append(i.capitalize()) # First letter uppercase

        return " ".join(res)
```

---

# Important Lines Explained

### Split the String

```python
tit = list(title.split(" "))
```

Splits the title into individual words.

Example:

```text
"i lOve leetcode"

↓

["i", "lOve", "leetcode"]
```

---

### Check Word Length

```python
if len(i) <= 2:
```

Words with length `1` or `2` must be completely lowercase.

---

### Convert Entire Word to Lowercase

```python
res.append(i.lower())
```

Examples:

```text
"OF" → "of"
"I"  → "i"
```

---

### Capitalize Long Words

```python
res.append(i.capitalize())
```

`capitalize()` converts:

- First letter → Uppercase
- Remaining letters → Lowercase

Examples:

```text
"tHe" → "The"
"EACH" → "Each"
```

---

### Join Words Back

```python
return " ".join(res)
```

Combines all processed words into a single string.

Example:

```text
["First", "Letter", "of", "Each", "Word"]

↓

"First Letter of Each Word"
```

---

# Dry Run

Input:

```text
title = "First leTTeR of EACH Word"
```

| Word | Length | Transformation |
|--------|--------|--------|
| First | 5 | First |
| leTTeR | 6 | Letter |
| of | 2 | of |
| EACH | 4 | Each |
| Word | 4 | Word |

Result:

```text
"First Letter of Each Word"
```

---

# Complexity Analysis

### Time Complexity

```text
O(n)
```

Where `n` is the length of the string.

---

### Space Complexity

```text
O(n)
```

For storing the transformed words.

---

# Key Learning

- String Manipulation
- String Splitting
- Case Conversion
- Traversing Words
- Built-in String Functions

---

# Tags

`String` `Simulation` `LeetCode 2129`