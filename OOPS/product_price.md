```
import java.util.*;
class product{
    int id;
    int price;
    int pro_quant;
    product(int id,int price,int pro_quant){
        this.id=id;
        this.price=price;
        this.pro_quant=pro_quant;
    }
}
public class products {
    public static void main(String args[]){
        product arr[]=new product[3];
        product p1=new product(1,20,3);
        arr[0]=p1;
        product p2=new product(2,30,2);
        arr[1]=p2;
        product p3=new product(3,40,1);
        arr[2]=p3;
        System.out.println("enter how many products u bought");
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int sum=0;
       int i=n;
       while(i>0){
           System.out.println("which product");
           int pro_id=sc.nextInt();
           System.out.println("enter quantity");
           int quant=sc.nextInt();
           product p=arr[pro_id-1];
           i=i-quant;
           switch(pro_id){
               case 1:
                   sum+=quant*p.price;
                   break;
               case 2:
                   sum+=quant*p.price;
                   break;
               case 3:
                   sum+=quant*p.price;
                   break;
           }
       }
        System.out.println(sum);
    }
}
```
