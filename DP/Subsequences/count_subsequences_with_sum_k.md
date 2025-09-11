# count subsequences with sum K
 
[Problem Link](https://takeuforward.org/plus/dsa/problems/count-subsets-with-sum-k)

# recurrsion

```
import java.util.*;
public class count_subsets_with_k {
  static int find(int []arr,int i,int n,int sum,int target){
      if(sum==target){
          return 1;
      }
      if(i>=n){
          return 0;
      }
      int left=find(arr,i+1,n,sum+arr[i],target);
     int right= find(arr,i+1,n,sum,target);
     return left+right;
  }

    public static void main(String[] args) {
        int arr[]={1,2,3,4,5};
        int sum=0;
        int target=5;
        System.out.println(find(arr,0,arr.length,sum,target));
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)
