# Best Time to Buy and Sell Stock

## Problem Statement

You are given an array `prices` where `prices[i]` is the price of a stock on the `i-th` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different future day to sell that stock.

Return the maximum profit you can achieve. If no profit is possible, return `0`.

---

## Example 1

### Input

```text
prices = [7,1,5,3,6,4]
```

### Output

```text
5
```

### Explanation

Buy on day 2 at price `1` and sell on day 5 at price `6`.

Profit = `6 - 1 = 5`

---

## Example 2

### Input

```text
prices = [7,6,4,3,1]
```

### Output

```text
0
```

### Explanation

No profitable transaction can be made because the stock price keeps decreasing.

---

# Approach 1: Two Pointer Technique

## Idea

* `i` represents the buying day.
* `j` represents the selling day.
* If a lower price is found, update the buying day.
* Continuously track the maximum profit.

## Code

```python
prices = list(map(int, input().split()))

max_prof = 0      # Stores maximum profit found so far
prof = 0          # Stores current profit

i, j = 0, 1       # i = buy day, j = sell day

while i < j and j < len(prices):

    if prices[i] < prices[j]:          # Profit possible
        prof = prices[j] - prices[i]   # Current profit
        max_prof = max(prof, max_prof) # Update maximum profit

    else:
        i = j                          # Found a better buying price

    j += 1                             # Move sell pointer

print(max_prof)                        # Final answer
```

### Time Complexity

```text
O(n)
```

### Space Complexity

```text
O(1)
```

---

# Approach 2: Minimum Price Tracking

## Idea

Keep track of the minimum stock price seen so far and calculate the profit if sold on the current day.

## Code

```python
class Solution:
    def stockBuySell(self, nums, n):

        prevVal = float("inf")  # Minimum price seen so far
        maxDiff = 0             # Maximum profit found so far

        i = 0

        while i < len(nums):

            if nums[i] <= prevVal:
                prevVal = nums[i]      # Update minimum buying price

            if nums[i] > prevVal:
                diff = nums[i] - prevVal   # Profit if sold today
                maxDiff = max(maxDiff, diff)  # Update best profit

            i += 1                     # Move to next day

        return maxDiff                 # Return maximum profit
```

### Time Complexity

```text
O(n)
```

### Space Complexity

```text
O(1)
```

---

# Dry Run

Input:

```text
[7,1,5,3,6,4]
```

| Day | Price | Minimum Price | Profit | Max Profit |
| --- | ----- | ------------- | ------ | ---------- |
| 1   | 7     | 7             | 0      | 0          |
| 2   | 1     | 1             | 0      | 0          |
| 3   | 5     | 1             | 4      | 4          |
| 4   | 3     | 1             | 2      | 4          |
| 5   | 6     | 1             | 5      | 5          |
| 6   | 4     | 1             | 3      | 5          |

Final Answer:

```text
5
```

---

# Key Learning

* Greedy Algorithm
* Two Pointer Technique
* Tracking Minimum Value
* Single Pass Array Traversal
* Maximum Profit Optimization

---

# Tags

`Array` `Greedy` `Two Pointers` `LeetCode 121`
