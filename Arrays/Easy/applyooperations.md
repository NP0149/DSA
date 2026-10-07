# Apply operations on array

[problem link](https://leetcode.com/problems/apply-operations-to-an-array/?envType=daily-question&envId=2025-03-01)


```
class Solution {
    public int[] applyOperations(int[] arr) {
        for(int i=0;i<arr.length-1;i++){
            if(arr[i]==arr[i+1]){
                arr[i]=2*arr[i];
                arr[i+1]=0;
            }
        }
       int j=0;
       for(int i=0;i<arr.length;i++){
         if(arr[i]!=0){
            arr[j]=arr[i];
            j++;
         }
       }
        while(j<arr.length){
            arr[j]=0;
            j++;
        }
        return arr;
    }
}
```
