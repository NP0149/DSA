# Products Distribution at a store

[Problem Link](https://leetcode.com/problems/minimized-maximum-of-products-distributed-to-any-store/description/)

# Approach-I

```
class Solution {
    public static int fun(int arr[],int limit,int k){
        int n=arr.length;
        int sum=0;
        int count=1;
        for(int i=0;i<n;i++){
         int temp=arr[i]/limit;
         if(arr[i]%limit!=0){
            temp++;
         }
        //  int temp=(int)Math.ceil((double)arr[i]/limit);
             k-=temp;
             if(k<0){
                return 0;
             }
        }     
        return 1;
    }
    public int minimizedMaximum(int k, int[] arr) {
        int low=1;
        int n=arr.length;
        int high=Integer.MIN_VALUE;
       for(int i=0;i<n;i++){
        high=Math.max(high,arr[i]);
       }
       while(low<=high){
        int mid=low+(high-low)/2;
        int t=fun(arr,mid,k);
        if(t==1){
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

Time:O(log n)

Space:O(1)
