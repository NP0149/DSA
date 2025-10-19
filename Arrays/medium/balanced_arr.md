# Balanced Array

[Problem link](https://leetcode.com/problems/longest-balanced-subarray-i/)

# Approach-I

```
import java.util.*;

public class balanced_arr {
    static int find(int arr[]){
        int n=arr.length;
        int maxlen=0;
        for(int i=0;i<n;i++){
            HashSet<Integer> evenset=new HashSet<>();
            HashSet<Integer> oddset=new HashSet<>();
            int even=0;
            int odd=0;
            for(int j=i;j<n;j++){
                int num=arr[j];
                if(arr[j]%2==0){
                    evenset.add(num);
                }
                else{
                    oddset.add(num);
                }
              if(evenset.size()==oddset.size()){
                  maxlen=Math.max(maxlen,j-i+1);
              }
            }
        }
        return maxlen;
    }
    public static void main(String[] args) {
        int arr[]={10,6,10,7};
        System.out.println(find(arr));
    }
}

```

# Complexities

Time:O(n)->best case and O(n^2)->worst case

Space:O(n)
