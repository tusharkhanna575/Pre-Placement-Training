# Assignment - II
# Topic - Arrays

## Question - I
### Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2),..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.

**Example :**
```
Input: nums = [1,4,3,2]
Output: 4
Explanation: All possible pairings (ignoring the ordering of elements) are:
1. (1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3
2. (1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3
3. (1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4

So, the maximum possible sum is 4
```

#### Code
```
int arrayPairSum(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    int maxSum = 0;
    for (int i = 0; i < nums.size(); i += 2) {
        maxSum += nums[i];
    }
    return maxSum;
}
```
- Time Complexity : $O(n*logn)$
- Space Complexity : $O(1)$
---

## Question - II
### Alice has `n` candies, where the `ith` candy is of type `candyType[i]`. Alice noticed that she started to gain weight, so she visited a doctor. The doctor advised Alice to only eat `n/2` of the candies she has (`n` is always even). Alice likes her candies very much, and she wants to eat the maximum number of different types of candies while still following the doctor's advice. Given the integer array candyType of length `n`, return the maximum number of different types of candies she can eat if she only eats `n/2` of them.

**Example :**
```
Input: candyType = [1,1,2,2,3,3]
Output: 3
Explanation: Alice can only eat 6/2 = 3 candies. Since there are only 3 types, she can eat one of each type.
```
#### Code
```
int distributeCandies(vector<int>& candyType) {
    set<int> s;
    for (int i = 0; i < candyType.size(); i++) {
        s.insert(candyType[i]);
    }
    int unique_candies = s.size();
    return min(unique_candies, (int) candyType.size()/2);
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(n)$
---
