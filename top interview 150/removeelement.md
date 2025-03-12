# Remove Element

[Problem Link](https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150)

```
class Solution {
    public int removeElement(int[] nums1, int val) {
       int nums2[]=new int[nums1.length];
       int k=0;
       int t=0;
       for(int i=0;i<nums1.length;i++){
        if(nums1[i]!=val){
            nums2[t]=nums1[i];
            t++;
            k++;
        }
       }
       for(int j=0;j<nums1.length;j++){
        nums1[j]=nums2[j];
       }
      return k;
       }
}
```
