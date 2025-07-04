# Allocate Minimum Pages

[Problem Link](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

# Approach-I

1)low=0 and high=sum(array) and then the answer lies in between

2)isvalid function is needed,in that we needed mid value and count if count > max pages then move eliminate left half if count<=max Pages

Then we needed less value so move to high=mid-1


```

//Back-end complete function Template for Java

class Solution {
    public static int isvalid(int arr[],int mid,int k){
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
    public static int findPages(int[] arr, int k) {
        // code here
        if(k>arr.length){
            return -1;
        }
        int low=0;
        int high=0;
        int n=arr.length;
        for(int i=0;i<n;i++){
            high+=arr[i];
        }
        
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int total=isvalid(arr,mid,k);
            if(total==1){
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

Time:O(n * Log n)

Space:O(1)
