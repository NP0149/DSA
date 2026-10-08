[Problem Link](https://www.geeksforgeeks.org/problems/smallest-number-subset1220/1)


# Not a subset sum

```
class Solution {
    public int findSmallest(int[] arr) {
        Arrays.sort(arr);
        if(arr[0]!=1){
            return 1;
        }
        int sum=0;
       for(int i=0;i<arr.length;i++){
           if(sum+1<arr[i]){
               return sum+1;
           }
           sum+=arr[i];
       }
       return sum+1;
    }
}
```
