# Aggressive cows

[Problem Link](https://www.geeksforgeeks.org/problems/aggressive-cows/1)

```
// User function Template for Java
class Solution {
    public static int isvalid(int arr[],int mid,int k){
        int count=1;
        int last=arr[0];
        for(int i=1;i<arr.length;i++){
      if((arr[i]-last)>=mid){
          count++;
          last=arr[i];
      }
        }
        if(count>=k){
            return 1;
        }
        else{
        return 0;
        }
    }
    public static int aggressiveCows(int[] arr, int k) {
        // code here
        Arrays.sort(arr);
        int low=1;
        int n=arr.length;
        int high=arr[n-1]-arr[0];
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int t=isvalid(arr,mid,k);
            if(t==1){
                ans=mid;
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return ans;
    }
}
```

# Complexities

Time:O(n log n)

Space:O(1)
