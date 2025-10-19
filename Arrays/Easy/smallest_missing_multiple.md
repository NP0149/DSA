# Smallest Missing multiple of k in an array

[Problme Link](https://leetcode.com/problems/smallest-missing-multiple-of-k/)


# Approach-I

```
class Solution {
    public int missingMultiple(int[] arr, int k) {
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            if(arr[i]%k==0){
                hm.put(arr[i],1);
            }
        }
        int num=0;
        for(int i=1;i<Integer.MAX_VALUE;i++){
            if(!hm.containsKey(i*k)){
                num=i*k;
                break;
            }
        }
        return num;
    }
}
```

# Complexities

Time:O(n)

Space:O(n)
