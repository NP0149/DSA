# Second Maximum in an array

# Approach-I

```
class Solution {
    public int secondLargestElement(int[] arr) {
       int max=Integer.MIN_VALUE;
       int prev=0;
       int secmax=-1;
       int n=arr.length;
       for(int i=0;i<n;i++){
        if(max<arr[i]){
            max=arr[i];
        }
       }
       for(int i=0;i<n;i++){
        if(arr[i]>secmax && arr[i]!=max){
            secmax=arr[i];
        }
       }
       return secmax;
    }
}
```
# Complexities

Time:O(n);

Space:O(1)


