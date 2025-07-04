# Painters Partition

[Problem Link](https://www.geeksforgeeks.org/problems/the-painters-partition-problem1535/1)

# Approach-I

Same as Book allocation

```
// User function Template for Java

class Solution {
    public static int isvalid(int []arr,int mid,int k){
        int count=1;
        int sum=0;
        for(int i=0;i<arr.length;i++){
            if(arr[i]>mid){
                return 0;
            }
            if(sum+arr[i]>mid){
                count++;
                sum=arr[i];
                
            }
            else{
                sum+=arr[i];
            }
        }
        if(count<=k){
            return 1;
        }
        else{
            return 0;
        }
    }
    public int minTime(int[] arr, int k) {
        // code here
        int low=0;
        int high=0;
        for(int i=0;i<arr.length;i++){
            high+=arr[i];
        }
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int t=isvalid(arr,mid,k);
            if(t==1){
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

Time:O(n*log N)

Space:O(1)
