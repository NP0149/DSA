[Problem Link](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

```
class Solution {
    public int evalRPN(String[] s) {
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<s.length;i++){
        if(s[i].equals("*") || s[i].equals("+") || s[i].equals("/") || s[i].equals("-")){
          int a=st.pop();
          int b=st.pop();
         if(s[i].equals("*")){
            int sum=a*b;
            st.push(sum);
         }
         else if(s[i].equals("-")){
            int sum=b-a;
            st.push(sum);
         }
         else if(s[i].equals("/")){
            int div=b/a;
            st.push(div);
         }
         else{
            int sum=a+b;
            st.push(sum);
         }
        }
       else{
        int num=Integer.parseInt(s[i]);
        st.push(num);
       }
        }
        return st.pop();
    }
}
```
