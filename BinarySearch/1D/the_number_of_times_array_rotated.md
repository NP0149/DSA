# The number of times the array is rotated

# Approach-I

1)first find the minimum in the array and then return its index

```
class Solution {
    public int findKRotation(ArrayList<Integer> list) {
        int n=list.size();
        int arr[]=new int[n];
      for(int i=0;i<n;i++){
      arr[i]=list.get(i);
      }
      int idx=-1;
      int low=0;
      int high=n-1;
      int mini=Integer.MAX_VALUE;
      while(low<=high){
        int mid=(low+high)/2;
        if(arr[low]<=arr[high]){
           if(arr[low]<=mini){
            idx=low;
           }
           break;
        }
        if(arr[low]<=arr[mid]){
            if(arr[low]<=mini){
            idx=low;
           }
            low=mid+1;
        }
        else{
            if(arr[mid]<=mini){
            idx=mid;
           }
            high=mid-1;
        }
      }
      return idx;
    }
}
```
# Complexties

Time:O(n)//because in the question they have given us Array List if the array is guven then it would be O(log N) as we have used binary search here

Space:O(n)//new array is being created
