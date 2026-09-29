```
import java.util.*;

public class duplicate {

    public static void main(String args[]){
        int arr[]={1,1,2,2,3,4,4};
        int j=0;
        for(int i=0;i<arr.length;i++){
            if(arr[i]!=arr[j]){
                j++;
                arr[j]=arr[i];
            }
        }
        for(int i=0;i<=j;i++){
            System.out.println(arr[i]);
        }
    }
}
```
