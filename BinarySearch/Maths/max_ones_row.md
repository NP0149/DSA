# Maximum number of ones in a row

[Problem Link](https://takeuforward.org/plus/dsa/problems/find-row-with-maximum-1's)

# Approach-I(Brute Force)

```
public class max_ones {
   public static int find(int mat[][]){
       int n=mat.length;
       int m=mat[0].length;
       int maxcount=-1;
       int indx=-1;
       for(int i=0;i<n;i++){
           int count=0;
           for(int j=0;j<m;j++){
               if(mat[i][j]==1){
                   count++;
               }
           }
          if(maxcount<count){
        maxcount=count;
        indx=i;
       }
}
      return indx;
   }
```
# Complexities

Time:O(n^2);

Space:O(1);

# Approach-II(Better)

1)u can send every row and then calculate the max value and then find the max row

```
class Solution {
  public static int find(int []arr){
    int n=arr.length;
    int count=0;
    for(int i=0;i<n;i++){
      if(arr[i]==1){
         count++;
      }
    }
    return count;
  }
    public int rowWithMax1s(int[][] mat) {
       int n=mat.length;
       int maxsum=Integer.MIN_VALUE;
       int indx=-1;
       for(int i=0;i<n;i++){
        int ans=find(mat[i]);
        if(maxsum<ans && ans!=0){
          maxsum=ans;
          indx=i;
        }
       }
       return indx;
    }
}
```
# Complexities

Time:O(n*m)

Space:O(1)
