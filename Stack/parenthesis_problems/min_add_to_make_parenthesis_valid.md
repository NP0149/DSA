# minimum number of additions to make the parenthesis valid

[Problem Link](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/?envType=daily-question&envId=2026-10-06)

```
class Solution {
    public int minAddToMakeValid(String s) {
        Stack<Character> st=new Stack<>();
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
         if(ch=='('){
            st.push(ch);
         }
         else{
            if(!st.isEmpty() && st.peek()=='('){
                st.pop();
            }
            else{
                st.push(ch);
            }
         }
        }
        return st.size();
    }
}
```
```
class Solution {
    public int minAddToMakeValid(String s) {
       int open=0;
       int close=0;
       for(int i=0;i<s.length();i++){
        char ch=s.charAt(i);
        if(ch=='('){
            open++;
        }
        else{
            if(open>0){
                open--;
            }
            else{
                close++;
            }
        }
       }
       return open+close;
    }
}
```
