# Merge Sort

[Problem Link](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)

```
class Solution {
    public void merge(int[] nums1, int n1, int[] nums2, int n2) {
       int i=0;
       int j=0;
        int k=0;
        int c[]=new int[n1+n2];
        while(i<n1 && j<n2){
            if(nums1[i]<=nums2[j]){
                c[k++]=nums1[i++];
            }
            else{
                c[k++]=nums2[j++];
            }
        }
        while(i<n1){
            c[k++]=nums1[i++];
        }
        while(j<n2){
            c[k++]=nums2[j++];
        }
        for(int t=0;t<n1+n2;t++){
            nums1[t]=c[t];
        }
    }
}
```
