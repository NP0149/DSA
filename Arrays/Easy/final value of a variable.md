# final value of a variable after performing certain functions over it in an array

[Problem Link](https://leetcode.com/problems/final-value-of-variable-after-performing-operations/submissions/1538247636/)

# Approach I

just comapre all the strings in character array with "++X" and "X++" then increment the X value by one if not decrease the value by one 


```Java
class Solution {
    public int finalValueAfterOperations(String[] op) {
        int n=op.length;
        int X=0;
        for(int i=0;i<n;i++){
            if(op[i].equals("++X")|| op[i].equals("X++")){
               X=X+1;
            }
            else{
              X=X-1;
            }
        }
        return X;
    }
}
```
# complexities

time complexity:O(N);

space complexity:O(1);
