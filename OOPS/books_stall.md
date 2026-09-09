```
import java.util.*;
class book{
    String name;
    int quant;
    book(String name,int quant){
        this.name=name;
        this.quant=quant;
    }
}
class customer{
    int id;
    String name;
    String book_name;
    customer(int id,String name,String book_name){
        this.id=id;
        this.name=name;
        this.book_name=book_name;
    }
}
public class bookstall {
    public static void main(String args[]){
        book book_arr[]=new book[2];
       book b1=new book("abc",3);
       book b2=new book("xyz",3);
       book_arr[0]=b1;
       book_arr[1]=b2;
        System.out.println("enter number of customers");
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
       for(int i=0;i<n;i++){
           int id=sc.nextInt();
           sc.nextLine();
           String name=sc.nextLine();
           String book_name=sc.nextLine();
           customer c=new customer(id,name,book_name);
           for(int j=0;j<book_arr.length;j++){
               if(book_name.equals(book_arr[j].name)){
                   book_arr[j].quant-=1;
               }
           }
       }
       for(int i=0;i<book_arr.length;i++){
           System.out.println(book_arr[i].name+" "+book_arr[i].quant);
       }
    }
}
```
