# Equal Partition 

[Problem Link](https://leetcode.com/problems/partition-equal-subset-sum/)


# Recurrsion

```
class Solution {
    static boolean find(int arr[],int i,int n,int target,int sum){
        if(sum==target){
            return true;
        }
        if(i>=n){
            return false;
        }
        if(find(arr,i+1,n,target,sum+arr[i])){
            return true;
        }
        if(find(arr,i+1,n,target,sum)){
            return true;
        }
        return false;
    }
    public boolean canPartition(int[] arr) {
        int n=arr.length;
        int sum=0;
        for(int i=0;i<n;i++){
            sum+=arr[i];
        }
       int target=sum/2;
       if(sum%2==0){
        return find(arr,0,n,target,0);
       }
       else{
        return false;
       }
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)
