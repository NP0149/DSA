# successfull binary searches irrespective of pivot

[Problem Link](https://www.geeksforgeeks.org/problems/count-always-found/1)


```
class Solution {
    public int countAlwaysFound(int[] arr) {
        // code here
        int prefix_max[]=new int[arr.length];
        int suffix_min[]=new int[arr.length];
        prefix_max[0]=Integer.MIN_VALUE;
        for(int i=1;i<arr.length;i++){
            prefix_max[i]=Math.max(prefix_max[i-1],arr[i-1]);
        }
        suffix_min[arr.length-1]=Integer.MAX_VALUE;
        for(int i=arr.length-2;i>=0;i--){
            suffix_min[i]=Math.min(suffix_min[i+1],arr[i+1]);
        }
        int count=0;
        for(int i=0;i<arr.length;i++){
            if(arr[i]>prefix_max[i] && arr[i]<suffix_min[i]){
                count++;
            }
        }
        return count;
    }
}
```
