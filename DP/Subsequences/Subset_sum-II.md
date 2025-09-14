# Subset sum

[Problem Link](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/description/)

# Usual Recurrsion

```
import java.util.*;
public class subset_sum {
    static boolean find(int arr[],int indx,int target){
        if(target==0){
            return true;
        }
        if(indx==0){
            return (arr[0]==target);
        }
        boolean notpick=find(arr,indx-1,target);
        boolean pick=false;
        if(arr[indx]<=target){
            pick=find(arr,indx-1,target-arr[indx]);
        }
        return pick || notpick;
    }
    public static void main(String[] args) {
        int arr[]={1,2,3,4};
        int target=6;
        System.out.println(find(arr,arr.length-1,target));
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)//recurrsion stack space
