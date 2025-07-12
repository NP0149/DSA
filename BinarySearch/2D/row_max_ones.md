# Row with max ones

[Problem Link](https://leetcode.com/problems/row-with-maximum-ones/submissions/1695141439/)

# Approach-I(Brute Force)

```
class Solution {
    public int[] rowAndMaximumOnes(int[][] arr) {
         int maxcount=0;
        int row=-1;
        int a[]=new int[2];
        for(int i=0;i<arr.length;i++){
            int count=0;
            for(int j=0;j<arr[0].length;j++){
                if(arr[i][j]==1){
                    count++;
                }
            }
            if(count>maxcount){
                row=i;
                maxcount=count;
                a[0]=row;
                a[1]=maxcount;
            }
        }
        return a;
    }
}
```
# Complexities

Time:O(m x n)//m is the row number and n is the column number

Space:O(1)
