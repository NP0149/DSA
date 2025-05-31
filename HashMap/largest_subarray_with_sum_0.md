# Largest Sub array with sum equals to 0

# Approach-I

1)Everytime calculate the prefix sum if prefix is equals to 0,then consider the max length 
2)everytime search for the sam prefix sum,by storing the values in hashmap and then check whether there is key or not
3)return the largest subarray length with sum equal to 0

```
import java.util.*;
public class largest_subarray {
    public static void main(String args[]) {
        int arr[] = {-1,-2,-3,6};
        int n = arr.length;
        int ps=0;
        int ls=0;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for (int i = 0; i < n; i++) {
         ps=ps+arr[i];
         if(ps==0){
             ls=  ls=Math.max(i+1,ls);
         }
        if(hm.containsKey(ps)){
            ls=Math.max(i-hm.get(ps)+1,ls);
        }
        else{
            hm.put(ps,i);
        }

        }

 System.out.println("the largest subarray with sum 0 is ="+ls);
    }
}
```

# Compelxities

Time:O(n);//n is the number of entries

Space:o(n);//to store every prefix sum equals to 0
