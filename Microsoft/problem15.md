# Problem: String Compression

## Problem Description

Given an array of characters chars, compress it using the following algorithm:

Begin with an empty string s. For each group of consecutive repeating characters in chars:

If the group's length is 1, append the character to s.
Otherwise, append the character followed by the group's length.
The compressed string s should not be returned separately, but instead, be stored in the input character array chars. Note that group lengths that are 10 or longer will be split into multiple characters in chars.

After you are done modifying the input array, return the new length of the array.

You must write an algorithm that uses only constant extra space.

 

Example 1:
Input: chars = ["a","a","b","b","c","c","c"]
Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Example 2:
Input: chars = ["a"]
Output: Return 1, and the first character of the input array should be: ["a"]

Example 3:
Input: chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
Output: Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

 

Constraints:

- 1 <= chars.length <= 2000
- chars[i] is a lowercase English letter, uppercase English letter, digit, or symbol.

SOLUTION

Language - C++

class Solution {
public:
    int compress(vector<char>& chars) {
        int n = chars.size();
        int index = 0;
        
        for(int i = 0; i < n; ) {
            char current = chars[i];
            int count = 0;
            
            while(i < n && chars[i] == current) {
                i++;
                count++;
            }
            
            chars[index++] = current;
            
            if(count > 1) {
                for(char c : to_string(count)) {
                    chars[index++] = c;
                }
            }
        }
        
        return index;
    }
};
