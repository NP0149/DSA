# longest consecutive subarray

```
class Solution {
    public int longestConsecutive(int[] arr) {
        HashSet<Integer> hs=new HashSet<>();
        for(int num:arr){
            hs.add(num);
        }
        int maxcount=0;
        for(int num:hs){
            if(!hs.contains(num-1)){
                int currnum=num;
                int currcount=1;
                while(hs.contains(currnum+1)){
                    currnum++;
                    currcount++;
                }
             maxcount=Math.max(currcount,maxcount);
            }
        }
        return maxcount;
    }
}
```
# complexities

Time:O(n)

Space:O(n)
