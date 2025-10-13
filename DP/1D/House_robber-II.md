# House Robber-II

[Problem Link](https://leetcode.com/problems/house-robber-ii/)


## Approach-I

same as house robber I just we need to run the function twice with last and without first and with first and without last
elements at the same time,as they are adjacent

```
class Solution {
    static int find(int n,int arr[]){
        if(n==0){
            return 0;
        }
        if(n==1){
            return arr[0];
        }
        if(n==2){
            return Math.max(arr[0],arr[1]);
        }
        int prev1=arr[0];
        int prev2=0;
        int curr=0;
        int pick=0;
        int notpick=0;
        for(int i=1;i<n;i++){
            pick=arr[i]+prev2;
            notpick=prev1;
            curr=Math.max(pick,notpick);
            prev2=prev1;
            prev1=curr;
        }
        return prev1;
    }
    public int rob(int[] arr) {
        int n=arr.length;
        int arr1[]=new int[n];
        int arr2[]=new int[n];
        int idx=0;
        int t=0;
        for(int i=0;i<n;i++){
      if(i!=0){
        arr1[idx++]=arr[i];
      }
      if(i!=n-1){
        arr2[t++]=arr[i];
      }
        }
        if(n==1){
            return arr[0];
        }
        return Math.max(find(n,arr1),find(n,arr2));
    }
}
```

## Complexity Analysis

Time:O(n)

Space:O(n)

## Approach-II(Optimal approach)

just call the function for 0 to n-2 excluding n-1 and then 1 to n-1


```
class Solution {
    static int find(int start,int end,int arr[]){
        int prev1=arr[start];
        int prev2=0;
        int pick=0,notpick=0;
        for(int i=start;i<end;i++){
            pick=arr[i]+prev2;
           notpick=prev1;
           int curr=Math.max(pick,notpick);
           prev2=prev1;
           prev1=curr;
        }
        return prev1;

    }
    public int rob(int[] arr) {
        int n=arr.length;
        int m1=find(0,n-1,arr);
        int m2=find(1,n,arr);
        return Math.max(m1,m2);
    }
}
```

## Complexity Analysis

Time:O(n)

Space:O(1)

```
import java.util.*;
public class house_robber_2 {
    static int find(int arr[],int start,int indx){
        if(indx==start){
            return arr[start];
        }
     if(indx<start){
         return 0;
     }
     int pick=find(arr,start,indx-2)+arr[indx];
     int notpick=find(arr,start,indx-1);
     return Math.max(pick,notpick);
    }
    static int find_mem(int arr[],int start,int indx,int []dp){
        if(indx==start){
            return arr[start];
        }
        if(indx<start){
            return 0;
        }
        if(dp[indx]!=-1){
            return dp[indx];
        }
        int pick=find_mem(arr,start,indx-2,dp)+arr[indx];
        int notpick=find_mem(arr,start,indx-1,dp);
        dp[indx]=Math.max(pick,notpick);
        return dp[indx];
    }
    static int find_tab(int arr[],int start,int indx,int end,int dp[]){
        int n=end-start+1;
       dp[0]=arr[start];
       dp[1]=Math.max(arr[start],arr[start+1]);
       for(int i=2;i<n;i++){
           dp[i]=Math.max(dp[i-1],dp[i-2]+arr[start+i]);
       }
       return dp[n-1];
    }

    public static void main(String[] args) {
        int arr[]={2,3,7};
       // System.out.println(Math.max(find(arr,0,arr.length-2),find(arr,1,arr.length-1)));
        System.out.println("using normal recurrsion");
        System.out.println(find(arr,0,arr.length-2));
        System.out.println(find(arr,1,arr.length-1));
        System.out.println("using memoisation");
        int dp[]=new int[arr.length];
        Arrays.fill(dp,-1);
        System.out.println(find_mem(arr,0,arr.length-2,dp));
        System.out.println(find_mem(arr,1,arr.length-1,dp));
        System.out.println("using tabulation");
        int d[]=new int[arr.length];
        System.out.println(find_tab(arr,0,arr.length-2,arr.length-2,d));
        System.out.println(find_tab(arr,1,arr.length-1,arr.length-1,d));
    }
}
```
