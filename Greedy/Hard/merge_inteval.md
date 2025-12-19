# Merging Interval

[Problem Link](https://leetcode.com/problems/merge-intervals/)

```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals,(a,b)->Integer.compare(a[0],b[0]));
        List<int[]>li=new ArrayList<>();
        for(int[] interval:intervals){
            if(li.isEmpty()){
                li.add(interval);
            }
            else if(li.get(li.size()-1)[1]>=interval[0]){
                if(li.get(li.size()-1)[1]<interval[1]){
                    li.get(li.size()-1)[1]=interval[1];
                }
                else{
                    continue;
                }
            }
            else{
                li.add(interval);
            }
        }
        int res[][]=li.toArray(new int[li.size()][]);
        return res;
    }
}
```
# Complexity Analysis

Time:O(n log n)

Space:O(n)
