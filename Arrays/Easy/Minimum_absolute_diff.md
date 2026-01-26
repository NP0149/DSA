# Minimum absolute difference

[Problem Link](https://leetcode.com/problems/minimum-absolute-difference/?envType=daily-question&envId=2026-01-26)

```
class Solution {
    public List<List<Integer>> minimumAbsDifference(int[] arr) {
        Arrays.sort(arr);
        
        List<List<Integer>> big=new ArrayList<>();
        int min=Integer.MAX_VALUE;
        for(int i=0;i<arr.length-1;i++){
            min=Math.min(min,(int)Math.abs(arr[i]-arr[i+1]));
        }
        for(int i=0;i<arr.length-1;i++){
            int res=(int)Math.abs(arr[i]-arr[i+1]);
            if(res==min){
                List<Integer> li=new ArrayList<>();
                li.add(arr[i]);
                li.add(arr[i+1]);
                big.add(li);
            }
        }
     return big;
    }
}
```

# Complexity Analysis

Time:O(N logN)

Space:O(1)
