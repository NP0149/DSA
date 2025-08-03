# Maze moving in all 4 directions

```
import java.util.*;
public class maze_inall{
  public static void path(int [][]maze,int r,int c,String p,int[][]path,int step){
      if(r==maze.length-1 && c==maze[0].length-1){
          for(int[] arr:path){
              System.out.println(Arrays.toString(arr));
          }
          System.out.println(p);
          System.out.println();
          System.out.println();
          return;
      }
      int m=maze.length-1;
      int n=maze[0].length-1;
      if(maze[r][c]==0){
          return;
      }
      maze[r][c]=0;
      path[r][c]=step;
      if(r<m){
          path(maze,r+1,c,p+'D',path,step+1);

      }
      if(c<n){
          path(maze,r,c+1,p+'R',path,step+1);

      }
      if(r>0){
          path(maze,r-1,c,p+"U",path,step+1);
      }
      if(c>0){
          path(maze,r,c-1,p+"L",path,step+1);

      }
      maze[r][c]=1;
      path[r][c]=0;
  }

    public static void main(String[] args) {
        int maze[][]={{1,1,1},{1,1,1},{1,1,1}};
        int [][]path=new int[maze.length][maze[0].length];
        path(maze,0,0,"",path,0);
    }
}



```

# Output

```
[0, 0, 0]
[1, 0, 0]
[2, 3, 0]
DDRR


[0, 0, 0]
[1, 4, 5]
[2, 3, 0]
DDRURD


[0, 5, 6]
[1, 4, 7]
[2, 3, 0]
DDRUURDD


[0, 0, 0]
[1, 2, 0]
[0, 3, 0]
DRDR


[0, 0, 0]
[1, 2, 3]
[0, 0, 0]
DRRD


[0, 3, 4]
[1, 2, 5]
[0, 0, 0]
DRURDD


[0, 1, 0]
[0, 2, 0]
[0, 3, 0]
RDDR


[0, 1, 0]
[0, 2, 3]
[0, 0, 0]
RDRD


[0, 1, 0]
[3, 2, 0]
[4, 5, 0]
RDLDRR


[0, 1, 2]
[0, 0, 3]
[0, 0, 0]
RRDD


[0, 1, 2]
[0, 4, 3]
[0, 5, 0]
RRDLDR


[0, 1, 2]
[5, 4, 3]
[6, 7, 0]
RRDLLDRR

```
