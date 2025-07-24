# Longest Consecutive Reapeated number

# Approach-I

1)consider k as 1 and then process it ,store the count of largest occuring

```
import java.util.*;
public class lon_con_repeated_num {
   public static int fun(int arr[]){
       int n=arr.length;
       int l=0;
       int ans=0;
       int key=0;
       HashMap<Integer,Integer> hm=new HashMap<>();
       for(int i=0;i<n;i++){
           int val=arr[i];
           hm.put(val,hm.getOrDefault(val,0)+1);
           while(hm.size()>1){
               int lval=arr[l];
               hm.put(lval,hm.getOrDefault(lval,0)-1);
               if(hm.get(lval)==0){
                   hm.remove(lval);
               }
               l++;
           }
           if(ans<hm.get(val)){
               key=val;
               ans=hm.get(val);
           }
       }
       System.out.println(key+"repeated for:"+ans+"times");
       return key;
   }

    public static void main(String[] args) {
        int arr[]={1,1,2,2,2,3,3,3,2,2,2,3,3,3,3,5,4,4,4,4,4,4,4,2,2};
        System.out.println(fun(arr));
    }
}

# Output
4
```

# Complexity Analysis

Time:O(n)

Space:O(n)
