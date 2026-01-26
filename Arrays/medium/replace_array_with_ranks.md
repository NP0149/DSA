# replace array with ranks

[Problem Link](https://www.geeksforgeeks.org/problems/replace-elements-by-its-rank-in-the-array/1)

```
// User function Template for Java

class Solution {
    static int[] replaceWithRank(int arr[], int N) {
        // code here
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            if(!hm.containsKey(arr[i])){
                hm.put(arr[i],i);
            }
        }
        List<Integer> li=new ArrayList<>();
        for(int num:hm.keySet()){
            li.add(num);
        }
        Collections.sort(li);
      for(int i=0;i<li.size();i++){
          hm.put(li.get(i),i+1);
      }
      int ans[]=new int[arr.length];
      for(int i=0;i<arr.length;i++){
          ans[i]=hm.get(arr[i]);
      }
      return ans;
    }
}
```

# Complexity Analysis

Time:O(NlogN)

Space:O(N)
