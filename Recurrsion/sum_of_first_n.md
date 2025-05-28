# Sum of first n 

```
import java.util.Scanner;
public class printsumoffirstn {
    public static int printsum(int n){
        int sum;
       if(n==0){
           return 0;
       }
       return n+printsum(n-1);
    }
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int m=printsum(n);
        System.out.println("the sum is  "+m);
    }
}

```

# complexities

Time:O(n);


# Approach -II


```
public static int printsum(int n){
int sum=0;
for(int i=0;i<=n;i++){
 sum+=i;
}
return sum;
}

```

# complexity

Time:o(1);
