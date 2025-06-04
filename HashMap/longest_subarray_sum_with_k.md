# Longest Subarray with sum k

[Problem Link](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)

1)traverse through the array add each element to the prefix sum.
2)store the prefix sum as key and index of an array as value
3)and then if ps is not contained then only add into the hashmap.//add the first occured
4)if ps-k is there then calculate the max length

```
// User function Template for Java

class Solution {
    public int longestSubarray(int[] arr, int k) {
        // code here
        HashMap<Integer,Integer> hm=new HashMap<>();
        int maxlen=0;
        int n=arr.length;
        int ps=0;
        for(int i=0;i<n;i++){
            ps+=arr[i];
            if(ps==k){
                maxlen=Math.max(i+1,maxlen);
            }
            if(!hm.containsKey(ps)){
                hm.put(ps,i);
            }
            if(hm.containsKey(ps-k)){
                maxlen=Math.max(maxlen,i-hm.get(ps-k));
            }
        }
        return maxlen;
    }
}
```

# Compelxties

time:O(n);


Space:O(n);
