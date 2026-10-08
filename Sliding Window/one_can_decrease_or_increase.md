# One can decrease or increase the adjacent numbers to make a number 


when there is no particular thing like u can only increase or u can only decrease so u can do both so

sort the array consider arr[mid] to make by increasing the lower numbers and decreasing the higher numbers and then count the frequency 
```
import java.util.*;

public class operations {

    public static void main(String args[]){
        int arr[]={1,2,4};
       Arrays.sort(arr);
       int l=0;
       long cost=0;
       long sum=0;
       int k=5;
       int maxsum=Integer.MIN_VALUE;
       for(int i=0;i<arr.length;i++){
           while(l<i){
               int mid=l+(i-l)/2;
              for(int j=l;j<=i;j++){
                  cost+=Math.abs((long)arr[i]-arr[mid]);
              }
              if(cost<=k){
                  break;
              }
               l++;
           }
           maxsum=Math.max(maxsum,i-l+1);
       }
        System.out.println(maxsum);
    }
}
```
