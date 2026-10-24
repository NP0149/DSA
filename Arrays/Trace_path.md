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

# Optimised

## here u need to to check the max path they travelled so that we are considering max row and min row and max col and min col of they are less than the mentioned row 

## and mentioned column then it is valid 

```
3. How do we get this intuition?
This is the most important part of the problem.

Imagine I give you a piece of string and ask you to place it inside a rectangular box.

The string follows a particular path, including all its turns.

You can move the entire string anywhere inside the box, but you cannot stretch it or change its shape.

What do you need to check?

You need to check whether the string fits inside the box.

You don't need to try placing it at every possible position. You only need to determine how much space it requires.

That is exactly what this problem is asking us to do with the movement path.
```

```
class Solution {
    public boolean isPossible(int n, int m, String s) {
        // code here
        int col=0;
        int row=0;
        int mincol=0;
        int minrow=0;
        int maxcol=0;
        int maxrow=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='L'){
                col-=1;
            }
            else if(ch=='R'){
                col+=1;
            }
            else if(ch=='U'){
                row-=1;
            }
            else if(ch=='D'){
                row+=1;
            }
            
            minrow=Math.min(minrow,row);
            maxrow=Math.max(maxrow,row);
            mincol=Math.min(mincol,col);
            maxcol=Math.max(maxcol,col);
        }
          return (maxrow-minrow<n) && (maxcol-mincol<m);
    }
}
```
