# Printing kadanes maximum subarray

```
import java.util.*;
public class kadanes {
    static int find(int arr[]){
        int currsum=arr[0];
        int maxsum=arr[0];
        int tempstart=-1;
        int start=-1;
        int end=-1;
        List<Integer> li=new ArrayList<>();
        for(int i=1;i<arr.length;i++){
            if(currsum+arr[i]<arr[i]){
                tempstart=i;
                currsum=arr[i];
            }
           else{
               currsum+=arr[i];
            }
           if(currsum>maxsum){
               maxsum=currsum;
               start=tempstart;
               end=i;
           }
        }
       for(int i=start;i<end;i++){
           System.out.println(arr[i]);
       }
        return maxsum;
    }
    public static void main(String[] args) {
        int arr[]={2,3,5,-2,7,-4};
        System.out.println(find(arr));
    }
}

```
