# Magnetic force between two magnets

[Problem Link](https://leetcode.com/problems/magnetic-force-between-two-balls/description/)

# Approach-I

```
class Solution {
    public static int fun(int arr[],int dis){
        int prev=arr[0];
        int count=1;
        for(int i=1;i<arr.length;i++){
            if(arr[i]-prev>=dis){
              prev=arr[i];
                count++;
            }
        }
        return count;
         
    }
    public int maxDistance(int[] arr, int m) {
        Arrays.sort(arr);
        int low=1;
        int high=arr[arr.length-1];
        int ans=-1;
        while(low<=high){
            int mid=low+(high-low)/2;
            int t=fun(arr,mid);
        if(t>=m){
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

Time:O(n*log n)

Space:O(1)
