# Split array largest sum

[Problem Link](https://leetcode.com/problems/split-array-largest-sum/description/)

# Approach-I

```
class Solution {
    public static int fun(int arr[],int k,int target){
        int n=arr.length;
        int sum=0;
        int count=1;
        for(int i=0;i<n;i++){
           if(arr[i]>target){
            return 0;
           }
           if(sum+arr[i]>target){
            count++;
            sum=arr[i];
           }
           else{
            sum+=arr[i];
           }
        }
       return count;
    }
    public int splitArray(int[] arr, int k) {
        int low=Integer.MIN_VALUE;
        int high=0;
        for(int i=0;i<arr.length;i++){
            low=Math.max(arr[i],low);
            high+=arr[i];
        }
        while(low<=high){
            int mid=low+(high-low)/2;
            int t=fun(arr,k,mid);
            if(t<=k){
              high=mid-1;
            }
            else{
               low=mid+1;
            }
        }
        return low;
    }
}
```

# Complexities

Time:O(n *log(high))

Space:O(1)
