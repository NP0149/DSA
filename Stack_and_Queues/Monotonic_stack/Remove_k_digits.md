# Remove k digits

[Problem Link](https://leetcode.com/problems/remove-k-digits/)

# Brute (But doesnot work for all testcases)

```
class Solution {
    public String removeKdigits(String s, int k) {
        int n=s.length();
        Long mini=Long.MAX_VALUE;
        if(s.length()==k){
            return "0";
        }
   for(int i=0;i<=n-k;i++){
    String sb=s.substring(0,i)+s.substring(i+k);
    if(sb.length()==0){
        continue;
    }
    Long a=Long.parseLong(sb);
     mini=Math.min(mini,a);
   }
   String l=Long.toString(mini);
   return l;
     }
}
```

# Complexity Analysis

Time:O(n^2)

Space:O(n)
