# Binary matrix 

[Problem Link](https://leetcode.com/problems/shortest-path-in-binary-matrix/description/)


# Approach-I

you need to move only through zeroes and can move in all 8 directions

```
class Solution {
    public static void path(int[][]maze,String p,int r,int c,ArrayList<String> li){
        int n=maze.length-1;
        int m=maze[0].length-1;
        if(maze[0][0]==1 || maze[n][m]==1){
            return;
        }
        if(r==n && c==m){
            li.add(p);
            return;
        }
        if(maze[r][c]==1){
            return;
        }
        if(maze[r][c]==2){
            return;
        }
        maze[r][c]=2;
      if(r>0){
          path(maze,p+'D',r-1,c,li);
      }
      if(r<n){
          path(maze,p+'D',r+1,c,li);
      }
      if(c>0){
          path(maze,p+'D',r,c-1,li);
      }
      if(c<m){
          path(maze,p+'D',r,c+1,li);
      }
      if(c>0){
          path(maze,p+'D',r,c-1,li);
      }
      if(r>0 && c>0){
          path(maze,p+'D',r-1,c-1,li);
      }
      if(r>0 && c<m){
          path(maze,p+'D',r-1,c+1,li);
      }
      if(r<n && c>0){
          path(maze,p+'D',r+1,c-1,li);
      }
      if(r<n && c<m){
          path(maze,p+'D',r+1,c+1,li);
      }
   maze[r][c]=0;
    }
    public int shortestPathBinaryMatrix(int[][] maze) {
        int mincount=Integer.MAX_VALUE;
        ArrayList<String> li=new ArrayList<>();
        path(maze,"",0,0,li);
        for(String s:li){
            if(mincount>s.length()){
                mincount=s.length();
            }
        }
        if(li.isEmpty()){
            return -1;
        }
        else{
        return mincount+1;
        }
    }
}
```

# Complexities

Time:O(8^N)

Space:O(8^N * N)//for storing all paths
