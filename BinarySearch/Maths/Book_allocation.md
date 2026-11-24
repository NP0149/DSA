# Allocate Minimum Pages

[Problem Link](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

# Approach-I

1)low=0 and high=sum(array) and then the answer lies in between

2)isvalid function is needed,in that we needed mid value and count if count > max pages then move eliminate left half if count<=max Pages

Then we needed less value so move to high=mid-1


```
class Solution {
    boolean find(int arr[],long mid,long k){
        long sum=0;
        long count=1;
        for(int i=0;i<arr.length;i++){
            if(arr[i]>mid){
                return false;
            }
            else if(sum+arr[i]<=mid){
                sum+=arr[i];
            }
            else{
               count++;
                sum=arr[i];
            }
        }
        if(count<=k){
            return true;
        }
        return false;
    }
    public int findPages(int[] arr, int k) {
        // code here
        if(arr.length<k){
            return -1;
        }
        long low=0;
        long high=0;
        for(int i=0;i<arr.length;i++){
            high+=arr[i];
        }
        long ans=-1;
        while(low<=high){
            long mid=low+(high-low)/2;
            if(find(arr,mid,(long)k)){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return (int)ans;
    }
}
```
# Complexities

Time:O(n * Log n)

Space:O(1)
