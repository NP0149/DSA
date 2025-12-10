# Next Smaller

[Problem Link](https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1)

```
class Solution {
    public int[] nextSmallerElements(int[] arr) {
        // Your code goes here
        int nse[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        int n=arr.length;
        for(int i=n-1;i>=0;i--){
            while(!st.isEmpty() && st.peek()>=arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                nse[i]=-1;
            }
            else{
                nse[i]=st.peek();
            }
            st.push(arr[i]);
        }
        return nse;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
