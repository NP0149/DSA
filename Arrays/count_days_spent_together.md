[Problem Link](https://leetcode.com/problems/count-days-spent-together/?envType=daily-question&envId=2026-10-24)

# counting number of days alice and bob are together

## count number of total days of alice and bob of their arrival and departure and after that find the maximum of arrival and minimum of departure so that will be 

## common time for them and then find the number of days

## if they are non overlapping then days become negative so in that case return 0


```
import java.util.*;


public class min_swaps {
    static int convert(String date,int []days){
        String parts[]=date.split("-");

        int m=Integer.parseInt(parts[0]);
        int d=Integer.parseInt(parts[1]);
        int total=0;
        for(int i=0;i<m-1;i++){
            total+=days[i];
        }
        total+=d;
        return total;

    }

   static int countdays(String arrivealice,String leavealice,String arrivebob,String leavebob){
       int days[]={31,28,31,30,31,30,31,31,30,31,30,31};
       int a1=convert(arrivealice,days);
       int a2=convert(leavealice,days);
       int b1=convert(arrivebob,days);
       int b2=convert(leavebob,days);
       int start=Math.max(a1,b1);
       int end=Math.min(a2,b2);
       return Math.max(0,end-start+1);

   }

    public static void main(String args[]){
       String arrivealice="08-15";
       String leavealice="08-18";
       String arrivebob="08-16";
       String leavebob="08-19";

       int days_together=countdays(arrivealice,leavealice,arrivebob,leavebob);
        System.out.println(days_together);

    }

}
```
