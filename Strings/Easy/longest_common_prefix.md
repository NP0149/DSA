# Longest common prefix

[Problem Link](https://leetcode.com/problems/longest-common-prefix/submissions/1886347327/)


```
class Solution {
    static String compare(String s,String lcp){
        StringBuilder newone=new StringBuilder();
        int i=0;
        int max=Math.min(s.length(),lcp.length());
        while(i<max && s.charAt(i)==lcp.charAt(i)){
            newone.append(s.charAt(i));
            i++;
        }
        return newone.toString();
    }
    public String longestCommonPrefix(String[] arr) {
        String lcp=arr[0];
        for(int i=1;i<arr.length;i++){
            String s=arr[i];
            lcp=compare(s,lcp);
        }
        return lcp;
    }
}
```
# Complexities

Time:O(n^2)

Space:O(1)
