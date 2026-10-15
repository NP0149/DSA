# Longest valid parenthesis

[Problem Link](https://leetcode.com/problems/longest-valid-parentheses/?envType=daily-question&envId=2026-10-03)


## first push -1 into the stack then if u have encounter opening parenthesis just push index value into the stack and if there is closing parenthesis then if stack is empty

## then we can say that there is no matching parenthesis for it so need to push that into the stack and after that u need to check the length of the string

```
class Solution {
    public int longestValidParentheses(String s) {
       Stack<Integer> st=new Stack<>();
       int maxlen=0;
       st.push(-1);
       for(int i=0;i<s.length();i++){
        char ch=s.charAt(i);
        if(ch=='('){
          st.push(i);
        }
        else{
         st.pop();
         if(st.isEmpty()){
            st.push(i);
         }
         else{
            maxlen=Math.max(maxlen,i-st.peek());
         }
        }
       }
       return maxlen;
    }
}
```
