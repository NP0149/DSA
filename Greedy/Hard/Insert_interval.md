# Insert Interval

[Problem Link](https://leetcode.com/problems/insert-interval/description/)

```
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<int[]> li=new ArrayList<>();
        for(int interval[]:intervals){
            li.add(interval);
        }
        li.add(newInterval);
        List<int[]> al=new ArrayList<>();
        Collections.sort(li,(a,b)->Integer.compare(a[0],b[0]));
        for(int[] interval:li){
            if(al.isEmpty()){
                al.add(interval);
            }
            else if(al.get(al.size()-1)[1]>=interval[0]){
                if(al.get(al.size()-1)[1]<interval[1]){
                    al.get(al.size()-1)[1]=interval[1];
                }
                else{
                    continue;
                }
            }
            else{
                al.add(interval);
            }
        }
        int result[][]=al.toArray(new int[al.size()][]);
        return result;
    }
}
```

# Complexity Analysis

Time:O(nlogn)

Space:O(n)
