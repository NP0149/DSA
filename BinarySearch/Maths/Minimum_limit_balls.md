# Minimum limit of balls

[Problem Link](https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/description/)

# Approach-I

```
class Solution {
    public static int fun(int arr[],int k,int m){
        for(int i=0;i<arr.length;i++){
         int temp=arr[i]/k;
         if(arr[i]%k!=0){
            temp++;
         }
         temp--;
         m-=temp;
        }
       if(m>=0){
        return 1;
       }
       else{
        return 0;
       }
    }
    public int minimumSize(int[] arr, int m) {
        int low=1;
        int high=(int)Math.pow(10,9);
        Arrays.sort(arr);
        int ans=-1;
        while(low<=high){
            int mid=low+(high-low)/2;
            int t=fun(arr,mid,m);
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

time:O(n * log n)

Space:O(1)
