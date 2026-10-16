# score of parenthesis

[Problem Link](https://leetcode.com/problems/score-of-parentheses/description/?envType=daily-question&envId=2026-10-05)

```
class Solution {
    public int scoreOfParentheses(String s) {
        Stack<Integer> st=new Stack<>();
        st.push(0);
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='('){
                st.push(0);
            }
            else{
                int a=st.pop();
                int b=st.pop();
                a=Math.max(2*a,1);
               st.push(a+b);
            }
        }
        return st.peek();
    }
}
```
