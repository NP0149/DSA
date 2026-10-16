# successfull binary searches irrespective of pivot

[Problem Link](https://www.geeksforgeeks.org/problems/count-always-found/1)



## the number is always included in searching when all the elements in the left are lesser than the number and all the elements in right are greater than the numebr

## so to check the condition just find the max value in left side and min value in the right side

## the left_max<arr[i]<right_max  ,so if this condition becomes true then the number is always included

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
