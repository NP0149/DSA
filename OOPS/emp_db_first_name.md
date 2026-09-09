```
import java.util.*;
class employee{
  String name;
  int age;
  int salary;
  employee(String name,int age,int salary){
      this.name=name;
      this.age=age;
      this.salary=salary;
  }
}
public class emp_db {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        HashMap<Character, List<employee>> hm = new HashMap<>();
        for (int i = 0; i < n; i++) {
            String name = sc.next();
            int age = sc.nextInt();
            int salary = sc.nextInt();
            employee e = new employee(name, age, salary);
            char ch = name.charAt(0);
            if (hm.containsKey(ch)) {
                hm.get(ch).add(e);
            } else {
                hm.put(ch, new ArrayList<employee>());
                hm.get(ch).add(e);
            }
        }
        for (char ch : hm.keySet()) {
            System.out.println(ch);
            for (employee e : hm.get(ch)) {
                System.out.println(e.name + " " + e.age + " " + e.salary);
            }
        }
        System.out.println("enter whose details u wanted");
        String name=sc.next();
        char ch=name.charAt(0);
        if(hm.containsKey(ch)){
           for(employee e:hm.get(ch)){
               if(e.name.equals(name)){
                   System.out.println(e.name+" "+e.age+" "+e.salary);
               }
           }
        }
        else{
            System.out.println("no employee found with that name");
        }
    }

}
```
