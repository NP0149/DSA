[Problem Link](https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150)


```

class Solution {
    public int removeElement(int[] arr, int val) {
        int j=0;
       for(int i=0;i<arr.length;i++){
        if(arr[i]!=val){
            arr[j]=arr[i];
            j++;
        }
       }
       return j;
    }
}
```
