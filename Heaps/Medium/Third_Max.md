# Third Max

[Problem Link](https://leetcode.com/problems/third-maximum-number/)

```
class Solution {
    public int thirdMax(int[]arr) {
        TreeSet<Integer> ts=new TreeSet<>();
        int max=Integer.MIN_VALUE;
        for(int i=0;i<arr.length;i++){
            ts.add(arr[i]);
            max=Math.max(max,arr[i]);
        }
        if(ts.size()<3){
            return max;
        }
        int indx=0;
        int need=ts.size()-3;
        int ans=max;
        for(int num:ts){
            if(indx==need){
                ans=num;
                break;
            }
            indx++;
        }
        return ans;
    }
}
```
