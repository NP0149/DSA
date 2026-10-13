# Maximum alternate square sum

[Problem Link](https://leetcode.com/problems/maximum-alternating-sum-of-squares/description/?envType=daily-question&envId=2026-10-13)



```
class Solution {
    public long maxAlternatingSum(int[] arr) {
        for(int i=0;i<arr.length;i++){
            arr[i]*=arr[i];
        }
        Arrays.sort(arr);
        long score=0;
        int mid=arr.length/2;
        for(int i=0;i<=mid-1;i++){
            score-=arr[i];
        }
        for(int i=mid;i<arr.length;i++){
            score+=arr[i];
        }
        return score;
    }
}
```
