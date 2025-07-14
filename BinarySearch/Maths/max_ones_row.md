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

# Approach-III(Optimal)

1)find lower bound ,so the lower bound becomes where 0 ends so form there we will be having only ones so that becomes the count

2)consider maxcount and that particula row

```
// Online Java Compiler
// Use this editor to write, compile and run your Java code online

class Main {
    public static int find(int arr[]){
        int low=0;
        int ans=-1;
        int n=arr.length;
        int high=n-1;
        int m=9999;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>=1){
                m=arr[mid];
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return ans;
    }
    public static void main(String[] args) {
  int arr[][]={{0,1,1},{1,1,1}};
  int m=arr[0].length;
  int maxones=-1;
  int indx=-1;
  for(int i=0;i<arr.length;i++){
      int r=arr[0].length-1-find(arr[i]);
   if(maxones<r){
       maxones=r;
       indx=i;
   }
  }
  System.out.println(indx);
    }
}
```

# Complexities

Time:O(m*logn)

Space:O(1)
