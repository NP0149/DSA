# There will be two seperate arrays we need to find the union of the arrays 

```
class Solution {
    public int[] unionArray(int[] nums1, int[] nums2) {
     Map<Integer,Integer> tm=new TreeMap<>();
     Set<Integer> ts1=new TreeSet<>();
     Set<Integer> ts2=new TreeSet<>();
        for(int i=0;i<nums1.length;i++){
            ts1.add(nums1[i]);
        }
        for(int i=0;i<nums2.length;i++){
            ts2.add(nums2[i]);
        }
        for(int num:ts1){
            if(tm.containsKey(num)){
                int prev=tm.get(num);
                tm.put(num,prev+1);
            }
            else{
                tm.put(num,1);
            }
    }
      for(int num:ts2){
           if(tm.containsKey(num)){
                int prev=tm.get(num);
                tm.put(num,prev+1);
            }
            else{
                tm.put(num,1);
            }
        }
     int count=0;
    for(int num:tm.keySet()){
        if(tm.get(num)>=2 || tm.get(num)==1){
            count++;
        }
    }
    int arr[]=new int[count];
    int j=0;
    for(int num:tm.keySet()){
        if(tm.get(num)>=2 || tm.get(num)==1){
            arr[j]=num;
            j++;
        }
    }
    return arr;
}
}
```

# Complexties

Time:O(nlogk+mlogk)


Space:O(n+m)


# Approach-II(Efficient)

```
import java.util.*;

class Solution {
    public int[] unionArray(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();

        // Add elements from both arrays
        for (int num : nums1) {
            set.add(num);
        }
        for (int num : nums2) {
            set.add(num);
        }

        // Convert set to array
        int[] result = new int[set.size()];
        int i = 0;
        for (int num : set) {
            result[i++] = num;
        }

        return result;
    }
}
```

# Complexities

Time:O(n+m);n is first array length and m is the second array length


Space:O(n+m)

