# Printing numbers in decreasing order

at first function print will be called if it doesnot equal to base condition,then it will print n and again function will be called
util it equals to base condition,in this way all the numbers will be printed from n to 0

```java
import java.util.*;
class main{
 public static void main(String args[]){
 Scanner sc=new Scanner(System.in);
 System.out.println("enter n");
 int n=sc.nextInt();
 System.out.println(print(n));
 
 }
 static int print(int n){
 if(n==0){
 return 0;
 }
 System.out.println(n);
 return print(n-1);
 }
 }
