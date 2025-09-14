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


# Memoization

```
import java.util.*;
public class subset_sum {
    static boolean find(int arr[],int indx,int target,Boolean dp[][]){
        if(target==0){
            return true;
        }
        if(indx==0) {
            return arr[0] == target;
        }
        if(dp[indx][target]!=null){
            return dp[indx][target];
        }

    boolean notpick=find(arr,indx-1,target,dp);
        boolean pick=false;
        if(arr[indx]<=target){
            pick=find(arr,indx-1,target-arr[indx],dp);
        }
        return pick || notpick;
    }
    public static void main(String[] args) {
        int arr[]={1,2,3,4};
        int target=6;
        Boolean dp[][]=new Boolean[arr.length][target+1];
        System.out.println(find(arr,arr.length-1,target,dp));
    }
}
```
# Complexity Analysis

Time:O(n*target)

Space:O(n*target) //for the array +O(n)//recurrsive stack space

# Tabulation
```
import java.util.*;
public class subset_sum {
    static boolean find(int arr[],int target){
        boolean dp[][]=new boolean[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=true;
        }
        if(arr[0]<=target){
            dp[0][arr[0]]=true;
        }
        for(int i=1;i<arr.length;i++){
            for(int j=1;j<=target;j++){
                boolean notpick=dp[i-1][j];
                boolean pick=false;
                if(arr[i]<=j){
                    pick=dp[i-1][j-arr[i]];
                }
                 dp[i][j]=pick|| notpick;
            }
        }
        return dp[arr.length-1][target];
    }
    public static void main(String[] args) {
        int arr[]={1,3,4};
        int target=6;
        System.out.println(find(arr,target));
    }
}
```
# Complexity Analysis

Time:O(n*target)

Space:O(n*target)
