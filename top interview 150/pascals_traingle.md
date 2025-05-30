# Pascals Triangle

[Problem Link](https://leetcode.com/problems/pascals-triangle/description/)

# Approach-I

1)its like printing a pattern

2)consider two loops because it inly ask for small n,so the TLE wont occur anyhow

3)in the second loop create a arraylist and then add ones based on j(j==0 or j==row) else add previous values and 
add to add previous values just create list in a list,so that you can access previous rows elements

```
class Solution {
    public List<List<Integer>> generate(int r) {
        List<List<Integer>> big=new ArrayList<>();
         for(int i=0;i<r;i++){
            List<Integer> inside=new ArrayList<>();
            for(int j=0;j<=i;j++){
               if(j==0 || j==i){
                inside.add(1);
               }
               else{
                inside.add(big.get(i-1).get(j-1)+big.get(i-1).get(j));
               }
            }
            big.add(inside);
           
         }
        
         return big;
    }
}
```

# Complexities

Time:O(r^2);

Space:O(r^2);


# Approach-II

1)we can use simple array to print pascals triangle 

```
import java.lang.reflect.Array;
import java.util.*;
public class al{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        System.out.println("enter n");
        int n=sc.nextInt();
       int arr[][]=new int[20][20];
        for(int i=0;i<n;i++){
            for(int j=0;j<=i;j++){
                if(i==0 || j==i || j==0){
                    arr[i][j]=1;
                    System.out.print("1 ");
                }
                else{
                    arr[i][j]=arr[i-1][j-1]+arr[i-1][j];
                  System.out.print(arr[i][j]+" ");
                }
            }
            System.out.println();
        }
    }
}
```

# Complexities

Time:O(n^2);

Space:O(1);
