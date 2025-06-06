# Count of Sub array sum equals to k ,the number of times subarray sum in an array equals to k

[Problem Link](https://leetcode.com/problems/subarray-sum-equals-k/submissions/1655800028/)

# Approach-I

```
class Solution {
    public int subarraySum(int[] arr, int k) {
        HashMap<Integer,Integer> hm=new HashMap<>();
        int n=arr.length;
        int ps=0;//prefix sum
        int count=0;
          if(arr.length==1){
            if(arr[0]!=k){
                return 0;
            }
        }
        for(int i=0;i<n;i++){
          ps+=arr[i];
//prefix sum equals to k then increase the count
          if(ps==k){
            count++;
          }
//prefix sum equals to ps-k,get the number of times it occured
           if(hm.containsKey(ps-k)){
                count+=hm.get(ps-k);
            }
//put the ele into the array with its frequencies
           if(hm.containsKey(ps)){
            hm.put(ps,hm.get(ps)+1);
           }
//just put number with count=1
           else{
            hm.put(ps,1);
           }
        }
    return count;
    }
    }
```

# Complexities

Time:O(n);

Space:O(n);//because of hashmap created for n elements
