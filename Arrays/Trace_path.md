[Problem Link](https://www.geeksforgeeks.org/problems/trace-path3840/1)


```
class Solution {
    boolean dfs(int row,int col,int n,int m,String s){
        int i=row;
        int j=col;
        for(int t=0;t<s.length();t++){
            char ch=s.charAt(t);
            if(ch=='L'){
                col=col-1;
            }
            else if(ch=='R'){
                col=col+1;
            }
            else if(ch=='U'){
                row=row-1;
            }
            else if(ch=='D'){
                row=row+1;
            }
            if(row<0 || row>=n || col<0 || col>=m){
                return false;
            }
        }
        return true;
    }
    public boolean isPossible(int n, int m, String s) {
        // code here
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(dfs(i,j,n,m,s)==true){
                    return true;
                }
            }
        }
        return false;
    }
}
```
