# Odd Number

[Problem Link](https://leetcode.com/problems/largest-odd-number-in-string/submissions/1659962275/)


```
class Solution {
    public String largestOddNumber(String num) {
        for (int i = num.length() - 1; i >= 0; i--) {
            char c = num.charAt(i);
            if ((c - '0') % 2 == 1) {
                return num.substring(0, i + 1);
            }
        }
        return "";
    }
}

```
# Complexities

Time:O(n);

space:O(1)
