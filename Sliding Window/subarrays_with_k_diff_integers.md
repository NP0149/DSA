# Subarrays with K different numbers

[Problem Link](https://leetcode.com/problems/subarrays-with-k-different-integers/)

# Approach-I

1)create a Hashmap if hashmap size is greater than k then decrement

2)return atmost(k)-atmost(k-1)

```
class Solution {
    public static int atmostk(int arr[],int k){
        int n=arr.length;
        int l=0;
        int ans=0;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<n;i++){
            int val=arr[i];
            hm.put(val,hm.getOrDefault(val,0)+1);
            while(hm.size()>k){
                int lval=arr[l];
                hm.put(lval,hm.get(lval)-1);
                if(hm.get(lval)==0){
                    hm.remove(lval);
                }
                l++;
            }
            ans+=i-l+1;
        }
        return ans;
    }
    public int subarraysWithKDistinct(int[] arr, int k) {
        return atmostk(arr,k)-atmostk(arr,k-1);
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
