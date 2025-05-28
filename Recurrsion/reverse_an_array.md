# Reverse an array

# Approach-I

```
import java.util.*;
public class revanarray {
    public static void rev(int arr[]){
        int n=arr.length;
        int brr[]=new int[5];
        for(int t=0;t<n;t++){
            brr[t]=arr[t];
        }
        int i=0;
        int j=n-1;
      while(i<n && j>=0){
          arr[i]=brr[j];
          i++;
          j--;
      }
        for(int k=0;k<n;k++){
            System.out.print(" "+arr[k]);
        }
    }
    public static void main(String args[]){
        int arr[]={1,2,3,4,5};
        rev(arr);
    }
}


```

# complexities

Time:O(n)

Space:O(n)   //extra array is used


# Approach-II

space is reduced to 1

```
import java.util.*;
public class revanarray {
    public static void rev(int arr[]){
        int n=arr.length;
        int i=0;
        int j=n-1;
      while(i<j){
          int temp=arr[i];
          arr[i]=arr[j];
          arr[j]=temp;
          i++;
          j--;
      }
        for(int k=0;k<n;k++){
            System.out.print(" "+arr[k]);
        }
    }
    public static void main(String args[]){
        int arr[]={1,2,3,4,5};
        rev(arr);
    }
}

```

# complexities

Time:O(n);

Space:O(1);  // extra array is not used


# Approach-III

```
import java.util.*;
public class revanarray {
    public static void rev(int arr[],int start,int end){
       if(start>=end){
           return;
       }
          int temp=arr[start];
          arr[start]=arr[end];
          arr[end]=temp;
          rev(arr,start+1,end-1);
      }
      public static void printarr(int arr[]){
        for(int i=0;i<arr.length;i++){
            System.out.print(" "+arr[i]);
        }
      }
    public static void main(String args[]){
        int arr[]={1,2,3,4,5};
        rev(arr,0,4);
        printarr(arr);
    }
}
```

# complexities

Time:O(n);

Space:O(1);
