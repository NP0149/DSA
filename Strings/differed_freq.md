# Difference frequency

[Problem Link](https://leetcode.com/contest/biweekly-contest-177/problems/smallest-pair-with-different-frequencies/description/)


```
class Solution {
    public int[] minDistinctFreqPair(int[] arr) {
        HashMap<Integer,Integer> hm=new HashMap<>();
            int smallest=Integer.MAX_VALUE;
        for(int i=0;i<arr.length;i++){
            hm.put(arr[i],hm.getOrDefault(arr[i],0)+1);
            smallest=Math.min(arr[i],smallest);
        }
        int ans[]=new int[2];
        ans[0]=smallest;
        int second=Integer.MAX_VALUE;
        for(int i=0;i<arr.length;i++){
            if(arr[i]<second && arr[i]!=smallest && hm.get(smallest)!=hm.get(arr[i])){
                second=arr[i];
            }
        }
        if(second!=Integer.MAX_VALUE){
            ans[1]=second;
        }
        else{
            ans[1]=-1;
        }
        if(ans[1]==-1){
            ans[0]=-1;
        }
        return ans;
    }
}
```
