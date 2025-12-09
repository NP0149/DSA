# Balanced Parenthesis

[Problem Link](https://leetcode.com/problems/valid-parentheses/)

```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> st=new Stack<>();
        int i=0;
        int n=s.length();
        while(i<n){
            char ch=s.charAt(i);
            if(ch=='(' || ch=='{' || ch=='['){
                st.push(ch);
            }
            else{
                if(st.isEmpty()){
                    return false;
                }
                else{
                    char ch1=st.peek();
                    if((ch1=='(' && ch!=')') || (ch1=='{' && ch!='}') || (ch1=='[' && ch!=']')){
                    return false;
                    }
                    else{
                        st.pop();
                    }
                }
            }
            i++;
        }
        return st.isEmpty();
    }
}
```

 # Complexity Analysis

 Time:O(n)

 Space:O(n)
