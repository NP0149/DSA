# print 1 to n

```
import java.util.Scanner;

public class printntimes{
    //n to 1
  public static void print(int n){
      if(n==0){
          return;
      }
      print(n-1);
      System.out.println(n);
  }

    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        print(n);
    }
}
```

# complexities

Time:O(n);

Space:O(n);
