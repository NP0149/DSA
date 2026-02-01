# Divide the array into subarrays

[Problem Link](https://leetcode.com/problems/divide-an-array-into-subarrays-with-minimum-cost-i/description/?envType=daily-question&envId=2026-02-01)


```
class Solution {
    public int minimumCost(int[] arr) {
        int first=arr[0];
        int min1=Integer.MAX_VALUE;
        int min2=Integer.MAX_VALUE;
        for(int i=1;i<arr.length;i++){
            if(min1>arr[i]){
                min2=min1;
                min1=arr[i];
            }
            else if(arr[i]<min2){
                min2=arr[i];
            }
        }
        return first+min1+min2;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)
