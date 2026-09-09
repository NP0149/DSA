```
import java.util.*;

public class prac {
    public static void main(String args[]){
//        int a=3;
//        int b=5;
//        char ch='/';
        Scanner sc=new Scanner(System.in);
        int a=sc.nextInt();
        int b=sc.nextInt();
        char ch=sc.next().charAt(0);
        int sum=0;
        switch(ch){
            case '+':
                sum=a+b;
                break;
            case '-':
                sum=a-b;
                break;
            case '*':
                sum=a*b;
                break;
            case '/':
                sum=a/b;
                break;
            default:
                System.out.println("please enter valid operation");
        }
        System.out.println(sum);
    }

}
```
