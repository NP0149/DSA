[Problem Link]()


```
import java.util.*;

public class p1 {

    public static void main(String args[]){
        int arr[]={1,1,2,2};
        int base=0;
        for(int i=0;i<arr.length-1;i++){
            if(arr[i]==arr[i+1]){
                base++;
            }
        }
        int left[]=new int[arr.length];
        for(int i=1;i<arr.length;i++){
            if(arr[i]==arr[i-1]){
                left[i]=-1;
            }
            else if((long) arr[i-1]-arr[i]==1){
                left[i]=1;
            }

        }
        int right[]=new int[arr.length];
        for(int i=0;i<arr.length-1;i++){
            if(arr[i]==arr[i+1]){
                right[i]=-1;
            }
            else if((long)arr[i+1]-arr[i]==1){
                right[i]=1;
            }
        }

        int prefix[]=new int[arr.length];
        prefix[0]=left[0];
        for(int i=1;i<arr.length;i++){
            prefix[i]=Math.max(prefix[i-1],left[i]);
        }
  int bestgain=0;
        for (int i=0;i<arr.length;i++){
            bestgain=Math.max(bestgain,prefix[i]+right[i]);
        }
        System.out.println(bestgain);
        System.out.println(base+bestgain);
    }
}
```
