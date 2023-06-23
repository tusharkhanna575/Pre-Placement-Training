# Assignment - II
# Topic - Arrays

## Question - I
### Given an integer array nums of 2n integers, group these integers into n pairs (a1, b1), (a2, b2),..., (an, bn) such that the sum of min(ai, bi) for all i is maximized. Return the maximized sum.

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

## Question - III
### We define a harmonious array as an array where the difference between its maximum value and its minimum value is exactly `1`. Given an integer array `nums`, return the length of its longest harmonious subsequence among all its possible subsequences. A subsequence of an array is a sequence that can be derived from the array by deleting some or no elements without changing the order of the remaining elements.

```
Input: nums = [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3]
```

#### Code
```
```
- Time Complexity : $O()$
- Space Complexity : $O()$
---

## Question - IV
### You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots. Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return `true` if `n` new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and `false` otherwise.

```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: true
```
#### Code
```
bool canPlaceFlowers(vector<int>& flowerbed, int n) {
    if (n==0) {
        return true;
    }
    for (int i = 0; i < flowerbed.size(); ++i) {
        if (flowerbed[i] == 0 && (i == 0 || flowerbed[i-1] == 0) && (i == flowerbed.size()-1 || flowerbed[i+1] == 0)) {
            flowerbed[i] = 1;
            n--;
            if (n == 0) {
                return true;
            }
        }
    }
    return false;
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(1)$
---

## Question - V
### Given an integer array nums, find three numbers whose product is maximum and return the maximum product.

```
Input: nums = [1,2,3]
Output: 6
```
#### Code
```

```
- Time Complexity : $O()$
- Space Complexity : $O()$
---

## Question - VI
### Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1. You must write an algorithm with O(log n) runtime complexity.
```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```
#### Code
```
int search(vector<int> &nums, int &n, int &target) {
    int low=0, high=n-1;
    int mid=low+(high-low)/2;
    while(low<=high) {
        if(nums[mid]<target) {
            low=mid+1;
        }
        else if(nums[mid]>target) {
            high=mid-1;
        }
        else {
            return mid;
        }
    }
    return low;
}
```
- Time Complexity : $O(logn)$
- Space Complexity : $O(1)$
---

## Question - VII
### An array is monotonic if it is either monotone increasing or monotone decreasing. An array nums is monotone increasing if for all i <= j, nums[i] <= nums[j]. An array nums is monotone decreasing if for all i <= j, nums[i] >= nums[j]. Given an integer array nums, return true if the given array is monotonic, or false otherwise.
```
Input: nums = [1,2,2,3]
Output: true
```
#### Code
```

```
- Time Complexity : $O()$
- Space Complexity : $O()$
---

## Question - VIII
### You are given an integer array nums and an integer k. In one operation, you can choose any index i where 0 <= i < nums.length and change nums[i] to nums[i] + x where x is an integer from the range [-k, k]. You can apply this operation at most once for each index i. The score of nums is the difference between the maximum and minimum elements in nums. Return the minimum score of nums after applying the mentioned operation at most once for each index in it. 
```
Input: nums = [1], k = 0
Output: 0
Explanation: The score is max(nums) - min(nums) = 1 - 1 = 0.
``` 
#### Code
```

```
- Time Complexity : $O()$
- Space Complexity : $O()$
---