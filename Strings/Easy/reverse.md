# Reverse of a string

[Problem Link](https://leetcode.com/problems/reverse-string/submissions/1703796027/)

```
class Solution {
    public void reverseString(char[] s) {
        int st=0;
        int end=s.length-1;
        while(st<end){
            char temp=s[st];
            s[st]=s[end];
            s[end]=temp;
            st++;
            end--;
        }
    }
}
```

# Complexities

Time:O(n)//length of the string

Space:O(1)
