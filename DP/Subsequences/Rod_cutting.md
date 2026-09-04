# Rod cutting

[Problem Link](https://www.geeksforgeeks.org/problems/rod-cutting0840/1)

# RECURRSION
```
class Solution {
    int find(int arr[],int n,int indx){
        if(indx==0){
            return n*arr[indx];
        }
        int nottake=find(arr,n,indx-1);
        int take=Integer.MIN_VALUE;
        if(indx+1<=n){
            take=arr[indx]+find(arr,n-(indx+1),indx);
        }
        return Math.max(take,nottake);
    }
    public int cutRod(int[] arr) {
      int n=arr.length;
      return find(arr,n,arr.length-1);
    }
}
```

# Memoisation

```
```
