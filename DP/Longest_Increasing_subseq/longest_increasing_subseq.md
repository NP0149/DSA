# Longest Increasing subsequence

[Problem Link](https://www.geeksforgeeks.org/problems/longest-increasing-subsequence-1587115620/1)

# Recurrsion

```
class Solution {
    int find(int arr[],int indx,int prev){
        if(indx>=arr.length){
            return 0;
        }
       int nottake=find(arr,indx+1,prev);
       int take=0;
       if(prev==-1 || arr[indx]>arr[prev]){
           take=1+find(arr,indx+1,indx);
       }
       return Math.max(take,nottake);
    }
    public int lis(int arr[]) {
        return find(arr,0,-1);
    }
}
```

