# LOngest subarray Majority greater than K

[Problem Link](https://www.geeksforgeeks.org/problems/longest-subarray-with-majority-greater-than-k/1)

```
class Solution {
    public int longestSubarray(int[] arr, int k) {
        // Code Here
        int maxlen=0;
        int prefix_sum=0;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            if(arr[i]>k){
                prefix_sum++;
            }
            else{
                prefix_sum--;
            }
            if(prefix_sum>0){
                maxlen=i+1;
            }
            else{
                if(hm.containsKey(prefix_sum-1)){
                    int indx=hm.get(prefix_sum-1);
                    maxlen=Math.max(maxlen,i-indx);
                }
            }
          if(!hm.containsKey(prefix_sum)){
              hm.put(prefix_sum,i);
          }
        }
        return maxlen;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
