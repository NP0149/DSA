# check if a string contains valid parenthesis

[Problem Link](https://leetcode.com/problems/valid-parentheses/submissions/2173081977/?envType=daily-question&envId=2026-10-01)

## declare a stack if open parenthesis comes just push them in to the stack if closing parenthesis comes just pop the character from only
## if it matches if not just return false
## after all these check if stack is empty ,if the string has valid parenthesis the stack automatically becomes empty so return if stack is empty


```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> st=new Stack<>();
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='(' || ch=='{' || ch=='['){
             st.push(ch);
            }
            else{
                if(st.isEmpty()){
                    return false;
                }
             else if(ch==')' && st.peek()!='('){
                return false;
             }
             else if(ch=='}' && st.peek()!='{'){
                return false;
             }
             else if(ch==']' && st.peek()!='['){
                return false;
             }
             st.pop();
            }
        }
        return st.isEmpty();
    }
}
```
