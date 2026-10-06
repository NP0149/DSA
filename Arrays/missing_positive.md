# Missing positive number though the repetitions and negative numbers are present


```
import java.util.*;

public class missing_pos {
   static int find(int arr[]){
       int n=arr.length;
    for(int i=0;i<arr.length;i++){
        if(arr[i]<=0){
            arr[i]=n+1;
        }
    }
    for(int i=0;i<arr.length;i++){
        int num=Math.abs(arr[i]);
        if(num<=n){
            arr[num-1]=-Math.abs(arr[num-1]);
        }
    }
    for(int i=0;i<arr.length;i++){
        if(arr[i]>0){
            return i+1;
        }
    }
    return n+1;
   }

    public static void main(String args[]){
        int arr[]={3,4,-1,1,1,1,1};

        System.out.println(find(arr));
    }
}

```
