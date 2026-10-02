
[Problem Link](https://leetcode.com/problems/rotate-string/)


```
class Solution {
    public boolean rotateString(String s, String goal) {
         StringBuilder sb=new StringBuilder(s);
         sb.append(s);
         String newstr=sb.toString();
         if(s.length()!=goal.length()){
            return false;
         }
         return newstr.contains(goal);
    }
}
```
