[Problem Link](https://leetcode.com/problems/largest-odd-number-in-string/)


```
class Solution {
    public String largestOddNumber(String str) {
     for(int i=str.length()-1;i>=0;i--){
        int num=str.charAt(i)-'0';
        if(num%2==1){
         return str.substring(0,i+1);
        }
     }
     return "";
    }
}
```
