# Next Greater element in circular Array


[Problem Link](https://leetcode.com/problems/next-greater-element-ii/)

```
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        Stack<Integer> st=new Stack<>();
        int nge[]=new int[nums.length];
        int n=nums.length;
        for(int i=2*n-1;i>=0;i--){
           int curr=nums[i%n];
           while(!st.isEmpty() && st.peek()<=curr){
            st.pop();
           }
           if(i<n){
         if(!st.isEmpty()){
            nge[i]=st.peek();
         }
         else{
            nge[i]=-1;
         }
           }
           st.push(curr);
         }
        return nge;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
