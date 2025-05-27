# GCD(greatest common divisor) or HCF(highest common factor)

```
import java.util.*;
public class gcd{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n1=sc.nextInt();
        int n2=sc.nextInt();
        while(n2!=0){
            int temp=n2;
            n2=n1%n2;
            n1=temp;
        }
        System.out.println(n1);
    }
}

```

# complexities

Time:O(1);


space:O(1);


very efficient
