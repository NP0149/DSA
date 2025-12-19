# Non Overlapping intervals

[Problem Link](https://leetcode.com/problems/non-overlapping-intervals/submissions/1859792038/)

# Brute force
```
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
          Arrays.sort(intervals,(a,b)->Integer.compare(a[1],b[1]));
        List<int[]>li=new ArrayList<>();
        int count=0;
        int overlap=0;
        for(int[] interval:intervals){
            if(li.isEmpty()){
                li.add(interval);
            }
            else if(li.get(li.size()-1)[1]>interval[0]){
                overlap++;
            }
            else{
                li.add(interval);
            }
        }
        return overlap;
    }
}
```
# Complexity Analysis

Time:O(nlog n)

Space:O(n)
