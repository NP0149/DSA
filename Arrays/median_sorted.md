[Problem Link](https://leetcode.com/problems/median-of-two-sorted-arrays/submissions/2173686731/?envType=study-plan-v2&envId=top-interview-150)


## I just created an array and then find whether the array size is odd or even if it is even then find mid and mid-1 if not just return the arr[mid]
```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int arr[]=new int[nums1.length+nums2.length];
        int i=nums1.length-1;
        int j=nums2.length-1;
        int k=arr.length-1;
        while(i>=0 && j>=0){
            if(nums1[i]>nums2[j]){
                arr[k--]=nums1[i--];
            }
            else{
                arr[k--]=nums2[j--];
            }
        }
        while(i>=0){
            arr[k--]=nums1[i--];
        }
        while(j>=0){
            arr[k--]=nums2[j--];
        }
        double median=0;
        if(arr.length%2==1){
            return arr[arr.length/2];
        }
        int mid=arr.length/2;
        int low=mid-1;
        median=(double)(arr[mid]+arr[low])/2;
        return median;
    }
}
```
