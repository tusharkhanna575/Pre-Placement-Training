# Assignment - I
# Topic - Arrays

## Question - I
### Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

**Example:**
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1]
```
#### Code
```
vector<int> targetSum(vector<int> &nums, int &n, int &target) {
    vector<int> ans(2,-1);
    for(int i=0;i<n;i++) {
        for(int j=i+1;j<n;j++) {
            if(nums[i]+nums[j]==target) {
                ans[0]=i;
                ans[1]=j;
                break;
            }
        }
    }
    return ans;
}
```
- Time Complexity : $O(n^2)$
- Space Complexity : $O(1)$

-----
## Question - II
### Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to `val`. Consider the number of elements in nums which are not equal to val be `k`, to get accepted, you need to do the following things:
- Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
- Return `k`.

**Example :**
```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2. It does not matter what you leave beyond the returned k (hence they are underscores)
```
#### Code
```
int removeElement(vector<int>& nums, int val) {
    int j = 0;
    for(int i = 0; i < nums.size(); i++){
        if(nums[i] != val){
            nums[j++] = nums[i];
        }
    }
    return j;
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(1)$

-----
## Question - III
### Given a sorted array of distinct integers `nums` and a `target` value, return the index if the `target` is found. If not, return the index where it would be if it were inserted in order. You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```
### Code
```
//using stl
int search(vector<int> &nums, int &n, int &target) {
    return(lower_bound(nums.begin(), nums.end(), target));
}
```
```
//without stl -> iterative
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
```
//without stl -> recursive
int search(vector<int> &nums, int low, int high, int &target) {
    int mid=low+(high-low)/2;
    if(nums[mid]>target) {
        search(nums,low,mid-1,target);
    }
    else if(nums[mid]<target) {
        search(nums,mid+1,high,target);
    }
    else {
        return mid;
    }
    return low;
}
```
- Time Complexity : $O(logn)$
- Space Complexity : $O(1)$
-----
## Question - IV
### You are given a large integer represented as an integer array `digits`, where each `digits[i]` is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's. Increment the large integer by one and return the resulting array of `digits`.

**Example :**
```
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123 Incrementing by one gives 123 + 1 = 124. Thus, the result should be [1,2,4]
```
#### Code
```
vector<int> addOne(vector<int> &digits) {
    for(int i=digits.size()-1;i>=0;i--) {
        if(digits[i]<9) {
            ++digits[i];
            return digits;
        }
        else {
            digits[i]=0;
        }
    }
    digits.push_back(0);
    digits[0]=1;
    return digits;
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(n)$
---
## Question - V
### You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively. Merge `nums1` and `nums2` into a single array sorted in non-decreasing order. The final sorted array should not be returned by the function, but instead be stored inside the array `nums1`. To accommodate this,
- `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. 
- `nums2` has a length of `n`.

**Example 1:**
```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6]. The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```
#### Code
```
//using sorting
void merge(vector<int> &nums1, int m, vector<int> &nums2, int n) {
    for (int j = 0, i = m; j<n; j++){
            nums1[i++] = nums2[j];
        }
    sort(nums1.begin(),nums1.end());
}
```
- Time Complexity : $O(n*logn)$
- Space Complexity : $O(1)$
```
//using two pointer approach
void merge(vector<int> &nums1, int m, vector<int> &nums2, int n) {
    int i=m-1, j=n-1, k=m+n-1;
    while(j>=0) {
        if(i>=0 && nums1[i]>nums2[j]) {
            nums1[k--]=nums1[i--];
        }
        else {
            nums1[k--]=nums2[j--];
        }
    }
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(1)$
---

## Question - VI
### Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct. 

**Example 1:**
```
Input: nums = [1,2,3,1]
Output: true
```
#### Code
```
//using stl
bool hasDuplicate(vector<int> &nums) {
    set<int> s(nums.begin(),nums.end());
    return((bool) (nums.size()==s.size()));
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(n)$
```
//not using stl
bool hasDuplicate(vector<int> &nums) {
    sort(nums.begin(),nums.end());
    for(int i=0;i<nums.size()-1;i++) {
        if(nums[i]==nums[i+1]) {
            return true;
        }
    }
    return false;
}
```
- Time Complexity : $O(n*logn)$
- Space Complexity : $O(1)$
---

## Question - VII
### Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the nonzero elements. Note that you must do this in-place without making a copy of the array.

**Example 1:**
```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```
#### Code
```
void moveZeros(vector<int> &nums) {
    int k=0;
    for(int i=0;i<nums.size();i++) {
        if(nums[i]!=0) {
            swap(nums[i],nums[k++]);
        }
    }
}
```
- Time Complexity : $O(n)$
- Space Complexity : $O(1)$
---
## Question - VIII
### You have a set of integers `s`, which originally contains all the numbers from `1 to n`. Unfortunately, due to some error, one of the numbers in `s` got duplicated to another number in the set, which results in repetition of one number and loss of another number. You are given an integer array `nums` representing the data status of this set after the error. Find the number that occurs twice and the number that is missing and return them in the form of an array.

**Example 1:**
```
Input: nums = [1,2,2,4]
Output: [2,3]
```
#### Code
```
vector<int> find(vector<int> &nums) {
    int dup=-1, miss=-1;
    for(int i=1;i<=nums.size();i++) {
        int count=0;
        for(auto j: nums) {
            if(i==j) {
                ++count;
            }
        }
        if(count==2) {
            dup=i;
        }
        else if(count==0) {
            miss=i;
        }
    }
    vector<int> ans={dup,miss};
    return ans;
}
```
- Time Complexity : $O(n^2)$
- Space Complexity : $O(1)$