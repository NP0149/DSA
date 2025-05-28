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

# pattern-II

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




