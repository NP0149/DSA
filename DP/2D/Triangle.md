# Triangle 

[Problem Link](https://leetcode.com/problems/triangle/)


# Usual Recurrsion

```
class Solution {
    static int find(List<List<Integer>> tri,int n,int i,int j){
        if(i==n-1){
            return tri.get(i).get(j);
        }
        int right=find(tri,n,i+1,j+1);
        int down=find(tri,n,i+1,j);
        return Math.min(right,down)+tri.get(i).get(j);
    }
    public int minimumTotal(List<List<Integer>> tri) {
        int n=tri.size();
        int i=0;
        int j=0;
        return find(tri,n,i,j) ;                   
    }
}
```

# Complexity Analysis

Time:O(n^2)

Space:O(n^2)

# Tabulation

