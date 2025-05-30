# Highest and lowest frequency in the array

# Approach-I

1) build a hashmap with array elements as key and their frequency as value and then store the highest occured key and lowest occured ke

```
import java.util.*;
public class hashing {
    public static void main(String args[]){
        int arr[]={2,2,3,4,4,2};
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            if(hm.containsKey(arr[i])){
                int prev=hm.get(arr[i]);
                hm.put(arr[i],prev+1);
            }
            else {
                hm.put(arr[i], 1);
            }
        }
      for(int key:hm.keySet()){
          System.out.println("the key is:"+key+"  the value is:"+hm.get(key));
      }
      int mini=Integer.MAX_VALUE;
      int minele=0;
      int maxele=0;
      int maxi=Integer.MIN_VALUE;
      for(int i=0;i<arr.length;i++){
         if(mini>hm.get(arr[i])){
             mini=hm.get(arr[i]);
             minele=arr[i];
         }
          if(maxi<hm.get(arr[i])){
              maxi=hm.get(arr[i]);
              maxele=arr[i];
          }
      }
      System.out.println("the max value is:"+maxele+"   the min value is:"+minele);
    }
}

```
# Complexities

Time:o(n);

Space:O(n);
