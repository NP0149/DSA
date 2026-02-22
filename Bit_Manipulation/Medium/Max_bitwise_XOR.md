# Maximum Bitwise XOR

[Problem Link](https://leetcode.com/problems/maximum-bitwise-xor-after-rearrangement/description/)

```
class Solution {
    public String maximumXor(String s, String t) {
        int count0=0;
        int count1=0;
       for(int i=0;i<s.length();i++){
         if(t.charAt(i)=='0'){
           count0++;
         }
         else{
            count1++;
         }
       }
       StringBuilder sb=new StringBuilder();
       int i=0;
      while(count1>0 && count0>0 && i<s.length()){
        if(s.charAt(i)!='0'){
         sb.append(0);
         count0--;
        }
        else{
            sb.append(1);
            count1--;
        }
     i++;
      }
      while(count1>0){
        sb.append(1);
        count1--;
      }
      while(count0>0){
        sb.append(0);
        count0--;
      }
     StringBuilder ans=new StringBuilder();
     for(int j=0;j<s.length();j++){
        ans.append(s.charAt(j)^sb.charAt(j));
     }
     return ans.toString();
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
