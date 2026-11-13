[Problem Link](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)

```
class Solution {
    public String removeDuplicates(String s) {
        Stack<Character> st=new Stack<>();
        int i=0;
        while(i<s.length()){
            char ch=s.charAt(i);
           if(!st.isEmpty() && st.peek()==ch){
            st.pop();
           }
           else{
            st.push(ch);
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
