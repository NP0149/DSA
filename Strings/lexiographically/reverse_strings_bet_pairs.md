[Problem Link](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses/description/)

```
class Solution {
    public String reverseParentheses(String s) {
        int i=0;
        Stack<Character> st=new Stack<>();
        while(i<s.length()){
            if(s.charAt(i)==')'){
              StringBuilder sb=new StringBuilder();
              while(!st.isEmpty() && st.peek()!='('){
                sb.append(st.pop());
              }
              st.pop();
              int k=0;
              while(k<sb.length()){
                st.push(sb.charAt(k));
                k++;
              }
            }
            else{
                st.push(s.charAt(i));
            }
            i++;
        }
      StringBuilder sb=new StringBuilder();
      while(!st.isEmpty()){
        sb.append(st.pop());
      }
      sb.reverse();
      return sb.toString();
    }
}
```
