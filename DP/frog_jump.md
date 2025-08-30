# Frog jump

## using usual method recurrsion to try out all possible ways

```
import java.util.*;
public class frog_jump {
    //usual method
  static int find(int []dp,int indx,int []arr){
      if(indx==0)
          return 0;
      if(dp[indx]!=-1){
          return dp[indx];
      }
      int left=find(dp,indx-1,arr)+Math.abs(arr[indx]-arr[indx-1]);
      int right=Integer.MAX_VALUE;
      if(indx>1){
          right=find(dp,indx-2,arr)+Math.abs(arr[indx]-arr[indx-2]);
      }
      return dp[indx]=Math.min(left,right);

  }

    public static void main(String[] args) {
       int h[]={2,1,3,5,4};
       int dp[]=new int[5];
       for(int i=0;i<5;i++){
           dp[i]=-1;
       }
        System.out.println("by using usual method");
        System.out.println(find(dp,h.length-1,h));
        System.out.println("when using ");
    }
}
```

## Complexity Analaysis

time:O(n)

Space:O(n)

## Using tabulation

```
  static int frog_jump_tab(int dp[],int n,int arr[]){
        dp[0]=0;
        int one=0;
        int two=0;
        for(int i=1;i<n;i++){
            one=dp[i-1]+Math.abs(arr[i]-arr[i-1]);
            two=Integer.MAX_VALUE;
            if(i>1){
                two=dp[i-2]+Math.abs(arr[i]-arr[i-2]);
            }
            dp[i]=Math.min(one,two);
        }
        return dp[n-1];
    }
```
## Complexity Analyisis

Time:O(n)

Space:O(n)

## Using Memoisation

```
 static int frog_jump_mem(int dp[],int n,int arr[]){
        if(n==0){
            return 0;
        }
        if(dp[n]!=-1){
            return dp[n];
        }
        int fs=frog_jump_mem(dp,n-1,arr)+Math.abs(arr[n]-arr[n-1]);
        int ss=Integer.MAX_VALUE;
        if(n>1)
        ss=frog_jump_mem(dp,n-2,arr)+Math.abs(arr[n]-arr[n-2]);
        dp[n]=Math.min(fs,ss);
        return dp[n];
    }
public static void main(String[] args) {
        int arr[]={2,5,1,7};
        int n=arr.length;
        int []dp=new int[n];
        for(int i=0;i<dp.length;i++){
            dp[i]=-1;
        }
        System.out.println(frog_jump_mem(dp,n-1,arr));
    }
```

## Complexity Analysis

Time:O(n)

Space:O(n)

## Optimal approach

```
    
    static int frog_jump_opt(int dp[],int n,int arr[]){
        int prev1=0;
        int prev2=0;
        for(int i=1;i<=n;i++){
            int one=prev1+Math.abs(arr[i]-arr[i-1]);
            int two=Integer.MAX_VALUE;
            if(i>1){
                two=prev2+Math.abs(arr[i]-arr[i-2]);
            }
            int curr=Math.min(one,two);
           prev2=prev1;
           prev1=curr;
        }
        return prev1;
    }
    public static void main(String[] args) {
        int arr[]={2,5,1,7};
        int n=arr.length;
        int []dp=new int[n];
        for(int i=0;i<dp.length;i++){
            dp[i]=-1;
        }
        System.out.println(frog_jump_opt(dp,n-1,arr));
    }
}
```
## Complexity Analysis

Time:O(n)

Space:O(1)
