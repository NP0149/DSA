# Power set

[Problem Link](https://leetcode.com/problems/subsets/description/)


# Approach-I

```
class Solution {
    public List<List<Integer>> subsets(int[] arr) {
        List<List<Integer>> al=new ArrayList<>();
        int n=arr.length;
        int l=(int)Math.pow(2,n);
        for(int i=0;i<l;i++){
           List<Integer> li=new ArrayList<>();
           for(int j=0;j<n;j++){
            if((i&(1<<j))!=0){
                li.add(arr[j]);
            }
           }
           al.add(li);
        }
        return al;
    }
}
```

# Complexity Analysis

Time:O(n*2^n)

Space:O(n*2^n)
