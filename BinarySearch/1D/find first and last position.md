# Find first and last position of an element in an array

[Problem Link](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)


# Approach-I

Using binary search

```
class Solution {
    public static int lower(int []arr,int target){
        int low=0;
        int n=arr.length;
        int high=n-1;
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>=target){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        if(ans!=-1 && arr[ans]==target)
        return ans;
        else
        return -1;
    }
     public static int upper(int []arr,int target){
        int low=0;
        int n=arr.length;
        int high=n-1;
        int ans=n;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>target){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        if(ans!=-1 && ans!=0 && arr[ans-1]==target)
        return ans-1;
        else
        return -1;
    }
    public int[] searchRange(int[] arr, int target) {
       int n[]=new int[2];
       if(arr.length==1 && arr[0]==target){
        n[0]=0;
        n[1]=0;
        return n;
       }
       n[0]=lower(arr,target);
       n[1]=upper(arr,target);
       return n;
    }
}
```

# Complexities

Time:O(log n)

Space;O(1)

# Approach-II
Asked to solve the problem in O(log n) complexity
But here it is O(n) complexitiy

```
class Solution {
    public int[] searchRange(int[] arr, int target) {
        //for the first occurance
        int n=arr.length;
        int newarr[]=new int[2];
        int pos=-1;
        newarr[0]=-1;
        newarr[1]=-1;
        for(int i=0;i<n;i++){
            if(arr[i]==target){
                newarr[0]=i;
                newarr[1]=i;
                  pos=i;
                  break;
            }
        }
        for(int i=0;i<n;i++){
            if(arr[i]==target && i!=pos){
                 newarr[1]=i;
            }
        }
        return newarr;
    }
}
```
# Complexities

Time:O(n);

Space:O(1)
