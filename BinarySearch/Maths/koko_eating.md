# koko eating

[Problem Link](https://leetcode.com/problems/koko-eating-bananas/)

```
class Solution {
    public static int fun(int []arr,int h,int mid){
        double total=0;
        for(int i=0;i<arr.length;i++){
        total+=Math.ceil((double)arr[i]/mid);
        }
        return (int)total;
    }
    public int minEatingSpeed(int[] arr, int h) {
        int low=1;
        int high=Integer.MIN_VALUE;
        int n=arr.length;
        for(int i=0;i<n;i++){
            high=Math.max(high,arr[i]);
        }
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int find=fun(arr,h,mid);
            if(find<=h){
               ans=mid;
               high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return ans;
    }
}
```
# Compelxities

Time:O(n*log(max(arr)))

Space:O(1)
