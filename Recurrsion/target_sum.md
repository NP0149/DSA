# Target sum out of all subsets from array

[Problem Link](https://www.geeksforgeeks.org/problems/count-the-subset-with-sum-equal-to-k/1)

```
class Solution {
    static int find_all(int arr[],int ind,int k){
       if (ind == arr.length) {
            return k == 0 ? 1 : 0;
        }
        int count=0;
        count+=find_all(arr,ind+1,k);
        if(arr[ind]<=k){
            count+=find_all(arr,ind+1,k-arr[ind]);
        }
        return count;
    }
    public int countSubset(int[] arr, int k) {
       return find_all(arr,0,k);
    }
}

```

# Complexity Analysis

Time:O(2^n)

Space:O(n)

