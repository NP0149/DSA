# Merge Sort

[Problem Link](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)

# Approach-I

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
# Complexties

Time:O(n1+n2)

Space:O(n1+n2)



# Approach-II(Efficient)

```
class Solution {
    public void merge(int[] nums1, int n1, int[] nums2, int n2) {
     int idx=n1+n2-1;
     int i=n1-1;
     int j=n2-1;
     while(i>=0 && j>=0){
        if(nums1[i]>nums2[j]){
            nums1[idx]=nums1[i];
            idx--;
            i--;
        }
        else{
            nums1[idx]=nums2[j];
            idx--;
            j--;
        }
     }
     while(j>=0){
        nums1[idx]=nums2[j];
        idx--;
        j--;
     }
}
}
```
# Complexities

Time:O(n1+n2)

Space:O(1)

