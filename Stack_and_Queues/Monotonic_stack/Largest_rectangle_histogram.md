# Largest Rectangle in histogram

[Problem Link](https://leetcode.com/problems/largest-rectangle-in-histogram/submissions/1853878161/)

```
class Solution {
    static int[] findnse(int arr[]){
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        int nse[]=new int[arr.length];
        for(int i=n-1;i>=0;i--){
            while(!st.isEmpty() && arr[st.peek()]>=arr[i]){
              st.pop();
            }
            if(st.isEmpty()){
                nse[i]=n;
            }
            else{
                nse[i]=st.peek();
            }
            st.push(i);
        }
        return nse;
    }
    static int[] findpse(int arr[]){
        int n=arr.length;
        int pse[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<n;i++){
            while(!st.isEmpty() && arr[st.peek()]>arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                pse[i]=-1;
            }
            else{
                pse[i]=st.peek();
            }
            st.push(i);
        }
        return pse;
    }
    public int largestRectangleArea(int[] arr) {
        int area=0;
        int n=arr.length;
        int nse[]=findnse(arr);
        int pse[]=findpse(arr);
        int max=Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
          int left=pse[i];
          int right=nse[i];
         int k=right-left-1;
         area=arr[i]*k;
         max=Math.max(max,area);
        }
        return max;
    }
}
```

# Complexities

Time:O(n)

Space:O(n)
