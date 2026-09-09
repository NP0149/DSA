```
import java.util.*;
class employee{
    String emp_name;
     int age;
     int salary;
     employee(String emp_name,int age,int salary){
         this.emp_name=emp_name;
         this.age=age;
         this.salary=salary;
     }
}

public class prac {
    public static void main(String args[]) {
        Scanner sc=new Scanner(System.in);
     int n=sc.nextInt();
     HashMap<Integer,employee> hm=new HashMap<>();
     for(int i=0;i<n;i++)
     {   String name=sc.next();
         int age=sc.nextInt();
         int salary=sc.nextInt();
         employee e=new employee(name,age,salary);
         hm.put(i+1,e);
     }
        System.out.println("enter the employee details u want to fetch");
        int m=sc.nextInt();
        employee e=hm.get(m);
        System.out.println(e.emp_name+" "+e.age+" "+e.salary);
    }
}
```
