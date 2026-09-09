# Account

```
import java.util.*;
class account{
    int acc_num;
    int acc_bal;
    account(int acc_num,int acc_bal){
        this.acc_num=acc_num;
        this.acc_bal=acc_bal;
    }
}

public class prac{
    static void credit(account arr[],int acc_num,int amount){
        arr[acc_num].acc_bal+=amount;
    }
    static boolean debit(account arr[],int acc_num,int amount){
        int acc_bal=arr[acc_num].acc_bal;
        if(amount>acc_bal){
            return false;
        }
        arr[acc_num].acc_bal-=amount;
        return true;
    }
    static void getbal(account arr[],int acc_num){
        System.out.println(arr[acc_num].acc_bal);
    }

    public static void main(String args[]){
        account arr[]=new account[3];
    account a1=new account(1,2000);
    account a2=new account(2,3000);
    account a3=new account(3,4000);
    arr[0]=a1;
    arr[1]=a2;
    arr[2]=a3;
    Scanner sc=new Scanner(System.in);
    int n=sc.nextInt();
   for(int i=0;i<n;i++){
       System.out.println("you want to debit:1,credit:2,balance:3");
       int type=sc.nextInt();
       if(type==1){
           System.out.println("enter account details");
           int acc_num=sc.nextInt();
           System.out.println("enter amount");
           int amount=sc.nextInt();
           if(debit(arr,acc_num-1,amount)) {
               System.out.println("money debited successfully");
               getbal(arr,acc_num-1);
           }
           else{
               System.out.println("u have less money than u are requesting");
           }

       }
       else if(type==2){
           System.out.println("enter account details");
           int acc_num=sc.nextInt();
           System.out.println("enter amount");
           int amount=sc.nextInt();
           credit(arr,acc_num-1,amount);
           getbal(arr,acc_num-1);
       }
       else{
           System.out.println("enter account details");
           int acc_num=sc.nextInt();
           getbal(arr,acc_num-1);
       }
   }
   for(int i=0;i<arr.length;i++){
       System.out.println(arr[i].acc_num+" ="+arr[i].acc_bal);
   }

    }

}

```
