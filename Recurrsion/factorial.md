# factorial of n

it doesnot work for big numbers
```
import java.util.Scanner;
public class printsumoffirstn {
    public static int factorial(int n){
        int sum;
       if(n==1){
           return 1;
       }
       return n*factorial(n-1);
    }
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int m=factorial(n);
        System.out.println("the factorial is  "+m);
    }
}

```


# complexities


Time:O(n);



# Approach-II


for big numbers we use this


```
import java.math.BigInteger;
import java.util.Scanner;

public class bigfact {

    public static BigInteger factorial(int n) {
        BigInteger result = BigInteger.ONE;
        for (int i = 2; i <= n; i++) {
            result = result.multiply(BigInteger.valueOf(i));
        }
        return result;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        BigInteger fact = factorial(n);
        System.out.println("The factorial is " + fact);
    }
}
```


# Complexities


Time:O(n * log n * log n);

space:O(n*logn);
