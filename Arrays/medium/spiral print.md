# Spiral Print

[problem link](https://leetcode.com/problems/spiral-matrix/description/)

# Approch

If you wanna traverse a row you need to focus on columns anf if You wanna traverse a column you need to focus on rows
every time you travel from minimum row to maximum row and minimum column to maximum column and every time you need increase the minimum row and column by 1 and decrease the maximum row and column by 1


```Java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> al=new ArrayList<>();
        int n=matrix.length;
        int m=matrix[0].length;
        int top=0;
        int left=0;
        int right=m-1;
        int bottom=n-1;
        while(top<=bottom && left<=right){
            for(int i=left;i<=right;i++){
                al.add(matrix[top][i]);
            }
            top++;
            for(int i=top;i<=bottom;i++){
                al.add(matrix[i][right]);
            }
            right--;
            if(top<=bottom){
            for(int i=right;i>=left;i--){
                al.add(matrix[bottom][i]);
            }
            bottom--;
            }
            if(left<=right){
            for(int i=bottom;i>=top;i--){
                al.add(matrix[i][left]);
            }
            left++;
            }
        }
        return al;
    }
}
```
# complexity analysis

 time complexity:O(N)
 
 space complexity:O(1)
 
