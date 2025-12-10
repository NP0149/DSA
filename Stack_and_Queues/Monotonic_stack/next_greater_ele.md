# Next Greater element

[Problem Link](https://leetcode.com/problems/next-greater-element-i/submissions/1851928084/)

```
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
     Stack<Integer> st=new Stack<>();
     int nge[]=new int[nums2.length];
     int n=nums2.length;
     for(int i=n-1;i>=0;i--){
        while(!st.isEmpty() && st.peek()<=nums2[i]){
            st.pop();
        }
        if(st.isEmpty()){
            nge[i]=-1;
        }
        else{
            nge[i]=st.peek();
        }
      st.push(nums2[i]);
     }
     Map<Integer,Integer> map=new HashMap<>();
     for(int i=0;i<nums2.length;i++){
        map.put(nums2[i],nge[i]);
     }
     int ans[]=new int[nums1.length];
     for(int i=0;i<nums1.length;i++){
        ans[i]=map.get(nums1[i]);
     }
     return ans;
    }
}
```
# Compplexities

Time:O(n)

Space:O(n)
