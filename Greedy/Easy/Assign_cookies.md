# Assign Cookies

[Problem Link](https://leetcode.com/problems/assign-cookies/)

```
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        int n=g.length;
        int m=s.length;
        int l=0;
        int r=0;
        Arrays.sort(g);
        Arrays.sort(s);
        while(l<n && r<m){
            if(g[l]<=s[r]){
                l++;
            }
            r++;
        }
       return l;
    }
}

```
# Complexity Analysis

Time:O(nlogn+mlogm)

Space:O(1)

