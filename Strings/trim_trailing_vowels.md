# Trim trailing vowels

[Problem Link](https://leetcode.com/contest/weekly-contest-491/problems/trim-trailing-vowels/)

```
class Solution {
    public String trimTrailingVowels(String s) {
         StringBuilder sb=new StringBuilder(s);
       int i=s.length()-1;
        while(i>=0 &&(sb.charAt(i)=='a' || sb.charAt(i)=='e' || sb.charAt(i)=='i' || sb.charAt(i)=='o' || sb.charAt(i)=='u')){
            sb.deleteCharAt(i);
            i=sb.length()-1;
        }
        return sb.toString();
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
