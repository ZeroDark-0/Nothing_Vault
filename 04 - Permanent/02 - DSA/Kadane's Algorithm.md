---
date: 2025-04-19T20:54
tags: []
---

This Algorithm is the overlap of the other algorithm (particularly double pointer and sliding window).

It's a Dynamic Programming and a Greedy Algorithm.

This is the algorithm where we have a array and have to return an non-empty subarray with the largest sum(in this the array can have positive and negative integer)..

#### <code style="color:purple"> ***Note the Subarray is the continuous part of the that array***</code>

As a sample:


|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| 4   | -1  | 2   | -7  | 3   | 4   |


First the Brute force for this Problem:- O(n^2)

---

```python
def bruteForce(nums):
    maxSum = nums[0]

    for i in range(len(nums)):
        curSum = 0
        for j in range(i, len(nums)):
            curSum += nums[j]
            maxSum = max(maxSum, curSum)
    return maxSum
```

```c++
#include <vector>
#include <algorithm>

using std::vector;
using std::max;

// Brute Force: O(n^2)
int bruteForce(vector<int>& nums) {
    int maxSum = nums[0];

    for (int i = 0; i < nums.size(); i++) {
        int curSum = 0;
        for (int j = i; j < nums.size(); j++) {
            curSum += nums[j];
            maxSum = max(maxSum, curSum);
        }
    }
    return maxSum;
}
```

In the above code we are just making the subarray and check it every time from every element respectively..

### Kandane's Algo

As in this Algo we are we can divide the element of the array into it own perspective position meaning the current element only know about the sum from the previous elements..

Also the negative element mean that will never increase the max sum..

and in this we take two element 'curr_ele' and 'sum'..
here we are add the element of the array into 'sum' and then comparing it to the 'curr_ele', if the curr_ele is greater the sum will be reassign to curr_ele value and if not it will continue adding the elements...

Meaning it will only take <code style="color:red">O(n)</code> time complexity..

Code for this algo:-

```python
def kadanes(nums):
    maxSum = nums[0]
    curSum = 0

    for n in nums:
        curSum = max(curSum, 0)
        curSum += n
        maxSum = max(maxSum, curSum)
    return maxSum

```

```c++
int kadanes(vector<int>& nums) {
    int maxSum = nums[0];
    int curSum = 0;

    for (int n : nums) {
        curSum = max(curSum, 0);
        curSum += n;
        maxSum = max(maxSum, curSum);
    }
    return maxSum;
}
```

This may be easy to find the max sum but what about returning the indexes..

As this algo use the Sliding Window and two Pointer, it will start from the 0th index of the array and we use to pointer name L and R also meaning L will never cross R (it can be equal) ..
It only grow the window until the ***curr_ele > sum*** and then it will reset the window to that element and start the window from there....

```python
def slidingWindow(nums):
    maxSum = nums[0]
    curSum = 0
    maxL, maxR = 0, 0
    L = 0

    for R in range(len(nums)):
        if curSum < 0:
            curSum = 0
            L = R

        curSum += nums[R]
        if curSum > maxSum:
            maxSum = curSum
            maxL, maxR = L, R 

    return [maxL, maxR]
    ```

```c++
vector<int> slidingWindow(vector<int> nums) {
    int maxSum = nums[0];
    int curSum = 0;
    int maxL = 0, maxR = 0;
    int L = 0;

    for (int R = 0; R < nums.size(); R++) {
        if (curSum < 0) {
            curSum = 0;
            L = R;
        }
        curSum += nums[R];
        if (curSum > maxSum) {
            maxSum = curSum;
            maxL = L; 
            maxR = R;     
        }    
    }    
    return vector<int>{maxL, maxR};
}   
```

/....
