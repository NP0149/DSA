# count subsequences with sum K
 
[Problem Link](https://takeuforward.org/plus/dsa/problems/count-subsets-with-sum-k)

# recurrsion

```
class Solution {
    
   static int find(int arr[],int target,int indx){
        if(indx==0){
            if(target==0 && arr[0]==0){
                return 2;
            }
            if(target==0 || arr[indx]==target){
                return 1;
            }
            return 0;
        }
        int nottake=find(arr,target,indx-1);
        int take=0;
        if(arr[indx]<=target){
            take=find(arr,target-arr[indx],indx-1);
        }
        return take+nottake;
    }
    static int perfectSum(int[] arr, int target) {
        return find(arr,target,arr.length-1);
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)
