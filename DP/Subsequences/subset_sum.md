# Subset Sum equal to target 

# Approach-I(Recurrsion)

```
import java.util.*;
public class generate_subsets {
    static void find_subsets(int arr[],int i,int n,List<Integer>li,int target,int sum){
        if(sum==target){
            System.out.println(li);
            return;
        }
        if(i>=n){
            return;
        }

        li.add(arr[i]);
        sum+=arr[i];
        find_subsets(arr,i+1,n,li,target,sum);
       int val= li.remove(li.size()-1);
       sum-=val;
        find_subsets(arr,i+1,n,li,target,sum);
    }

    public static void main(String[] args) {
        int arr[]={3,1,2};
        List<Integer> li=new ArrayList<>();
        int n=arr.length;
        int target=3;
        find_subsets(arr,0,n,li,target,0);
    }
}
```
# Complexity Analysis

Time:O(2^n) //2 times calling the same function in function

Space:O(n) //recurrsive stack


# memoisation and tabulation

```
class Solution {
    
    static boolean find_mem(int arr[],int indx,int target,boolean dp[][]){
        if(target==0){
            return true;
        }
        if(indx==0){
            return target==arr[0];
        }
        boolean nottake=find_mem(arr,indx-1,target,dp);
        boolean take=false;
        if(arr[indx]<=target){
            take=find_mem(arr,indx-1,target-arr[indx],dp);
        }
        dp[indx][target]=(take || nottake);
        return dp[indx][target];
        
    }
    static boolean find_tab(int arr[],int target){
        boolean dp[][]=new boolean[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=true;
        }
        if(arr[0]<=target){
            dp[0][arr[0]]=true;
        }
        
        for(int i=1;i<arr.length;i++){
            for(int j=1;j<=target;j++){
                boolean nottake=dp[i-1][j];
                boolean take=false;
                if(arr[i]<=j){
                    take=dp[i-1][j-arr[i]];
                }
                dp[i][j]=(take || nottake);
            }
        }
        return dp[arr.length-1][target];
        
    }
    static boolean isSubsetSum(int arr[], int target) {
        // boolean dp[][]=new boolean[arr.length][target+1];
    //   return  find_mem(arr,arr.length-1,target,dp);
     return find_tab(arr,target);
        
    }
}
```


