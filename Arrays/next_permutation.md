[Problem Link](https://www.geeksforgeeks.org/problems/next-permutation5226/1)


```
class Solution {
    void nextPermutation(int[] arr) {
        // code here
        int j=arr.length-2;
        int pivot=-1;
        while(j>=0){
            if(arr[j]<arr[j+1]){
                pivot=j;
                break;
            }
            j--;
        }
        
        if(pivot==-1){
            Arrays.sort(arr);
            return;
        }
      int indx=-1;
      int next_max=Integer.MAX_VALUE;
      for(int i=pivot+1;i<arr.length;i++){
          if(arr[i]>arr[pivot]){
              if(next_max>arr[i]){
                  indx=i;
                  next_max=arr[i];
              }
          }
      }
      int temp=arr[pivot];
      arr[pivot]=arr[indx];
      arr[indx]=temp;
        Arrays.sort(arr,pivot+1,arr.length);
    }
}
```
