# pattern-1


```
* * * *
* * * *
* * * *
* * * *

import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                System.out.print("*  ");
            }
            System.out.println();
        }
    }

        }
```

# pattern-2

```
*
* *
* * *
* * * *

import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                System.out.print("*  ");
            }
            System.out.println();
        }
    }

}
```

# pattern-3

```
* * * *
* * *
* *
*



import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<n-i;j++){
                System.out.print("*  ");
            }
            System.out.println();
        }
    }
}

```
# Pattern-4

```
1 
1 2 
1 2 3 



import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                System.out.print(j+1+" ");
            }
            System.out.println();
        }
    }
}
```
# Pattern-5

```
1 
2 2 
3 3 3 



import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<i;j++){
                System.out.print(i+" ");
            }
            System.out.println();
        }
    }
}
```

# Pattern-6

```
4 4 4 4 
3 3 3 
2 2 
1

import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=n;i>0;i--){
            for(int j=1;j<=i;j++){
                System.out.print(i+" ");
            }
            System.out.println();
        }
    }
}
```
# Pattern-7

```
4 3 2 1 
3 2 1 
2 1 
1 

import java.util.*;

public class pat_1{
    public static void main(String args[]){
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        for(int i=n;i>0;i--){
            for(int j=i;j>0;j--){
                System.out.print(j+" ");
            }
            System.out.println();
        }
    }
}
```
# Pattern-8

```
*********
 *******
  *****
   ***
    *
import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
        for (int i = n; i > 0; i--) {
            for(int t=0;t<n-i;t++){
                System.out.print(" ");
            }
            for (int j = 0; j < 2 * i - 1; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

    }
}
```
# Pattern-9

```
     *
    ***
   *****
  *******
 *********


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
        for (int i = 0; i<n; i++) {
            for(int t=0;t<n-i;t++){
                System.out.print(" ");
            }
            for (int j = 0; j < 2 * i +1; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

    }
}
```

# Pattern-10

```
5
    *
   ***
  *****
 *******
*********
*********
 *******
  *****
   ***
    *


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
        for (int i = 0; i<n; i++) {
            for(int t=0;t<n-i-1;t++){
                System.out.print(" ");
            }
            for (int j = 0; j < 2 * i +1; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
      for(int i=0;i<n;i++){
          for(int k=0;k<i;k++){
              System.out.print(" ");
          }
          for(int j=2*(n-i-1)+1;j>0;j--){
              System.out.print("*");
          }
          System.out.println();
        }

    }
}
```
# Pattern-11

```
5
*
**
***
****
*****
****
***
**
*

import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<=i;j++){
                System.out.print("*");
            }
            System.out.println();
        }
        for(int i=0;i<n;i++){
            for(int j=0;j<n-i-1;j++){
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```
# Pattern-12

```
1 
0 1 
1 0 1 
0 1 0 1 
1 0 1 0 1


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
        for(int i=0;i<n;i++){
            for(int j=0;j<=i;j++){
                if(i%2==0){
                    if(j%2==0)
                    System.out.print("1 ");
                    else{
                        System.out.print("0 ");
                    }
                }
                else{
                    if(j%2==0){
                        System.out.print("0 ");
                    }
                    else{
                        System.out.print("1 ");
                    }
                }
            }
            System.out.println();
        }
    }
}
```
# Pattern-13
```
1      1
12    21
123  321
12344321


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows and columns");
        int n = sc.nextInt();
       for(int i=0;i<n;i++){
           for(int j=0;j<=i;j++){
               System.out.print(j+1);
           }
           for(int t=2*(n-i-1);t>0;t--){
               System.out.print(" ");
           }
           for(int k=i+1;k>0;k--){
               System.out.print(k);
           }
           System.out.println();
       }
    }
}
```

# Pattern-14

```
1 
2 3 
4 5 6 
7 8 9 10 
11 12 13 14 15 


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                System.out.print(a+++" ");
            }
            System.out.println();
        }
    }
}
```
# Pattern-15
```
A
AB
ABC
ABCD
ABCDE


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                System.out.print((char)(65+j));
            }
            System.out.println();
        }
    }
}
```
# Pattern-16

```
ABCDE
ABCD
ABC
AB
A

import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <n-i; j++) {
                System.out.print((char)(65+j));
            }
            System.out.println();
        }
    }
}
```
# Pattern-17

```
A
BB
CCC
DDDD
EEEEE


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <=i; j++) {
                System.out.print((char)(65+i));
            }
            System.out.println();
        }
    }
}
```
# Pattern-18

```
    A
   ABA
  ABCBA
 ABCDCBA


import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for (int i = 0; i < n; i++) {
            for(int t=0;t<n-i;t++){
                System.out.print(" ");
            }
            for (int j = 0; j <=i; j++) {
                System.out.print((char)(65+j));
            }
            for(int k=i-1;k>=0;k--){
                System.out.print((char)(65+k));
            }
            System.out.println();
        }
    }
}
```
# Pattern-19
```
E
DE
CDE
BCDE
ABCDE

import java.util.*;
public class pat_1 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter number of rows");
        int n = sc.nextInt();
        int a = 1;
        for(int i=n;i>=0;i--){
            for(int j=i;j<n;j++){
                System.out.print((char)(65+j));
            }
            System.out.println();
        }
    }
}
```


