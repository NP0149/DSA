# maze problem 1

```
import java.util.*;
public class maze {
   public static int count(int r,int c){
       if(r==1 || c==1){
           return 1;
       }
       int left=count(r-1,c);
       int right=count(r,c-1);
       int diagonal=count(r-1,c-1);
       int total=left+right+diagonal;
       return total;
   }
 static void path(String p,int r,int c,ArrayList<String> li){
       if(r==1 && c==1){
           li.add(p);
           return;
       }
       //N is moving diagonally
       if(r>1 && c>1){
           path(p+'N',r-1,c-1,li);
       }
       //D is coming down
       if(r>1){
           path(p+'D',r-1,c,li);
       }
       //R is moving right
       if(c>1){
           path(p+'R',r,c-1,li);
       }
 }
    public static void main(String[] args) {
        System.out.println(count(3,3));
        ArrayList<String> li=new ArrayList<>();
        path("",3,3,li);
        System.out.println(li);
    }
}
```

# Complexities

Time:O(3^{r+c}*{r+c})

Space:O(3^{r+c}*{r+c})
