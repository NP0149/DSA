# Floor and ceil in sorted array

# Approach-I

we need to find the largest number that is less than the x(x is the given number),this is called as floor and smallest large number than x

this is called as ceil

```Java
 class Solution {
    public static int floor(int []nums,int x){
        int n=nums.length;
        int ans=-1;
        int low=0;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid]<=x){
                ans=mid;
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        if(ans==-1)
        return -1;
        else
        return nums[ans];
    }
      public static int ceil(int []nums,int x){
        int n=nums.length;
        int ans=-1;
        int low=0;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid]>=x){
                ans=mid;
                high=mid-1;
            }
            else{
               low=mid+1;
            }
        }
        if(ans==-1)
        return -1;
        else
        return nums[ans];
    }
    public int[] getFloorAndCeil(int[] nums, int x) {
       int n[]=new int[2];
       n[0]=floor(nums,x);
       n[1]=ceil(nums,x);
       return n;
    }
}
```
# Complexities

Time:O(logn)

Space:O(1)
