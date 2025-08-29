# Frog jump

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

