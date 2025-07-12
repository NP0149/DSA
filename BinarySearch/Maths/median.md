# Median of two sorted arrays

[Problem Link](https://leetcode.com/problems/median-of-two-sorted-arrays/submissions/1694911644/)

# Approach-I

1)take new array and then combine all the elements in the two arrays and then find the meadian by applying formula

2)even number of ele=(n/2)+(n/2-)/2  return arr[ele];

3)for odd return arr[n/2];

```
class Solution {
    public double findMedianSortedArrays(int[] a, int[] b) {
        int n1=a.length;
        int n2=b.length;
    int idx=n1+n2-1;
    int arr[]=new int[n1+n2];
    int i=n1-1;
    int j=n2-1;
    while(i>=0 && j>=0){
        if(a[i]>=b[j]){
            arr[idx--]=a[i--];
        }
        else{
            arr[idx--]=b[j--];
        }
    }
    while(i>=0){
        arr[idx--]=a[i--];
    }
    while(j>=0){
        arr[idx--]=b[j--];
    }
    int n=arr.length;
  int mid1=(n)/2;
  int mid2=mid1-1;
  if((n)%2==0){
    return (arr[mid1]+arr[mid2])/2.0;
  }
  else{
    return arr[mid1];
  }
    }
}
```
# Complexities

Time:O(n1+n2)

Space:O(n1+n2)
