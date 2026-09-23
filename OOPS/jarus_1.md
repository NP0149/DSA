```
import java.sql.Array;
import java.util.*;
abstract class Product{
    String proname;
    double proprice;
    public Product(String proname,double proprice){
        this.proname=proname;
        this.proprice=proprice;
    }
    public abstract double calfinalprice();
    public double getpriceafterdiscount(){
        return proprice-(proprice*0.10);
    }
}

class digitalpro extends Product{
    digitalpro(String name,double price){
        super(name,price);
    }
    public double calfinalprice(){
        double afterdis=getpriceafterdiscount();
        double tax=afterdis*0.18;
        return afterdis+tax;
    }
}
class physicalpro extends Product{
    physicalpro(String name,double price){
        super(name,price);
    }
    public double calfinalprice(){
        double afterdis=getpriceafterdiscount();
        double tax=afterdis*0.10;
        return afterdis+tax;
    }
}

public class jarus_1 {

    public static void main(String args[]){
        List<Product> cart=new ArrayList<>();
        cart.add(new digitalpro("soap",200));
        cart.add(new digitalpro("book",300));
        cart.add(new physicalpro("laptop stand",1200));
        
        double total=0;
        
        for(Product p:cart){
            double finalprice=p.calfinalprice();
            System.out.println(p.proname+" "+p.proprice+" "+finalprice);
            total+=finalprice;
        }
        System.out.println("total amount to be paid"+total);
    }

}
```
