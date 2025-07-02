# Capacity to ship packages within d days

[Problem Link](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/submissions/1684131919/)

# Approach-I

```
class Solution {
    public static int fun(int arr[],int mid){
        int n=arr.length;
        int sum=0;
        int count=1;
        for(int i=0;i<n;i++){
            if(sum+arr[i]>mid){
                count++;
               sum=arr[i];
            }
            else{
              sum+=arr[i];
            }
        }
        return count;
    }
    public int shipWithinDays(int[] arr, int days) {
        int low=Integer.MIN_VALUE;
        int n=arr.length;
        int high=0;
        for(int i=0;i<n;i++){
           high+=arr[i];
            low=Math.max(low,arr[i]);
        }
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int total=0;
            total=fun(arr,mid);
            if(total<=days){
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

# Complexities

Time:O(log n * N)

Space:O(1)
