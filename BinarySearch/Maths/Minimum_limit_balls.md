# Minimum limit of balls

[Problem Link](https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/description/)

# Approach-I

```
class Solution {
    int isvalid(int arr[],long mid,int maxop){
        int count=0;
        for(int i=0;i<arr.length;i++){
            count+=(arr[i]-1)/mid;
            if(count>maxop){
                return 0;
            }
        }
        return 1;
    }
    public int minimumSize(int[] arr,int maxop) {
        long low=1;
        long high=0;
        for(int i=0;i<arr.length;i++){
            high=Math.max(high,arr[i]);
        }
       long ans=-1;
        while(low<=high){
          long mid=low+(high-low)/2;
        int check=isvalid(arr,mid,maxop);
        if(check==1){
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

time:O(n * log n)

Space:O(1)
