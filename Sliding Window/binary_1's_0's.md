# Binary 1's and 0's 

[Problem Link](https://leetcode.com/problems/binary-subarrays-with-sum/)


# Approach-I

1)we need to move as we move in siding window and then ,we need to consider all the subarrays standing at that point,so we can say here we
are considering for sum<=goal,if sum>goal shrink the window size 

2)Increase the count and at last return count

3)return 0,if goal is less than 0,because in binary array it never sum to value less than 0

4)At last return fun(arr,goal)-fun(arr,goal-1)

```
class Solution {
    public static int fun(int arr[],int goal){
     int l=0;
     int sum=0;
     int n=arr.length;
     int count=0;
     for(int i=0;i<n;i++){
        sum+=arr[i];
        while(sum>goal && l<=i){
            sum-=arr[l];
            l++;
        }
        count+=i-l+1;
     }
     return count;
    }
    public int numSubarraysWithSum(int[] arr, int goal) {
        if(goal<0){
            return 0;
        }
        int a=fun(arr,goal);
        int b=fun(arr,goal-1);
    return a-b;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
