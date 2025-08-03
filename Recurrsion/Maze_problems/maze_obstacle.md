# rat is moving in maze with obstacle

```
import java.util.*;
public class maze_obstacle {
    public static void path(boolean maze[][],String p,int r,int c,ArrayList<String>li){
        if(r==maze.length-1 && c==maze[0].length-1){
          li.add(p);
            return ;
        }
        if(maze[r][c]==false){
            return;
        }
        if(r<maze.length-1){
           path(maze,p+"D",r+1,c,li);
        }
        if(c<maze[0].length-1){
            path(maze,p+"R",r,c+1,li);
        }
    }

    public static void main(String[] args) {
         boolean maze[][]={{true,true,true},{true,false,true},{true,true,true}};
         ArrayList<String> li=new ArrayList<>();
         path(maze," ",0,0,li);
        System.out.println(li);

    }
}
```

# Complexity Analysis

Time:O(2^{m + n})

Space:O(k * (m + n) + (m + n))
