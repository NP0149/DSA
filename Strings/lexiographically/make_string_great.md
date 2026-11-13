[Problem Link](https://leetcode.com/problems/make-the-string-great/submissions/2194975654/)

```
class Solution {
    public String makeGood(String s) {
     Stack<Character> st=new Stack<>();
      int i=0;
      while(i<s.length()){
        if(st.isEmpty()){
            st.push(s.charAt(i));
        }
        else{
            char ch=s.charAt(i);
            char top=st.peek();
            if((int)ch>90 && (int)top>90){
                st.push(s.charAt(i));
            }
            else if((int)top<=90 && (int)ch<=90){
                st.push(s.charAt(i));
            }
            else if((int)ch>90){
                if(Character.toLowerCase(top)==ch){
                    st.pop();
                }
                else{
                    st.push(ch);
                }
            }
            else if((int)ch<=90){
                if(Character.toUpperCase(top)==ch){
                    st.pop();
                }
                else{
                    st.push(ch);
                }
            }
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
