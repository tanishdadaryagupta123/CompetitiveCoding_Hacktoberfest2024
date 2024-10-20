#Problem : Largest subarray with 0 sum

## Problem Description

Given an array having both positive and negative integers. The task is to compute the length of the largest subarray with sum 0.

Example 1 : 
Input: arr[] = {15,-2,2,-8,1,7,10,23}, n = 8
Output: 5

Example 2 : 
Input: arr[] = {2,10,4}, n = 3
Output: 0

Example 3 : 
Input: arr[] = {1, 0, -4, 3, 1, 0}, n = 6
Output: 5

Constraints:
1 <= n <= 105
-1000 <= arr[i] <= 1000, for each valid i

SOLUTION

Language - C++

class Solution {
public:
    int maxLen(vector<int>& arr, int n) {
        unordered_map<int, int> prefixSumMap;
        int sum = 0, maxLength = 0;
        
        for(int i = 0; i < n; i++) {
            sum += arr[i];
            
            if(sum == 0) {
                maxLength = i + 1;
            } else if(prefixSumMap.find(sum) != prefixSumMap.end()) {
                maxLength = max(maxLength, i - prefixSumMap[sum]);
            } else {
                prefixSumMap[sum] = i;
            }
        }
        
        return maxLength;
    }
};
