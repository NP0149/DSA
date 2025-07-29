# Merge overlapping intervals

[Problem Link](https://leetcode.com/problems/merge-intervals/submissions/1715214945/)

# Approach-I

1)we need to sort the 2 D array by Arrays.sort(arr,(a,b)->compare(a[0],b[0])) 

2)create new arraylist to store merged intervals so create arraylist in this way li<int[]>

3)check if li is empty or previous interval[1]<current interval[0] so there is no chance of overlapping so just add interval as new interval in list

4)if the condition fails then just find the max of previous interval[1] and current interval[1] and then assign to previous interval
so this is the merging of intervals

```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals,(a,b)->Integer.compare(a[0],b[0]));
        List<int[]> li=new ArrayList<>();
        for(int [] interval :intervals){
            if(li.isEmpty() || li.get(li.size()-1)[1]<interval[0]){
                li.add(interval);
            }
            else{
                li.get(li.size()-1)[1]=Math.max( li.get(li.size()-1)[1],interval[1]);
            }
        }
       return li.toArray(new int[li.size()][]);
    }
}
```
# Complexity Analysis

Time:O(n * log n)->to sort the array

Space:O(n)->creating list of n size and also returning n size array
