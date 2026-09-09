[Problem link](https://leetcode.com/problems/daily-temperatures/)


```
class Solution {
    public int[] dailyTemperatures(int[] arr) {
        int ans[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        for(int i=arr.length-1;i>=0;i--){
            while(!st.isEmpty() && arr[st.peek()]<=arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                ans[i]=0;
            }
            else{
                ans[i]=Math.abs(i-st.peek());
            }
            st.push(i);
        }a
        return ans;
    }
}
```
