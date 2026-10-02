[Problem Link](https://leetcode.com/problems/reverse-words-in-a-string/submissions/2159819025/)


```
class Solution {
    public String reverseWords(String s) {
        String newstr=s.replaceAll("\\s+"," ");
        newstr=newstr.trim();
        Stack<Character> st=new Stack<>();
        for(int i=0;i<newstr.length();i++){
            st.push(newstr.charAt(i));
        }
        StringBuilder sb=new StringBuilder();
        StringBuilder temp=new StringBuilder();
        while(!st.isEmpty()){
            char ch=st.pop();
            if(ch!=' '){
                temp.append(ch);
            }
            else{
                temp.reverse();
                temp.append(" ");
                sb.append(temp);
                temp.setLength(0);
            }
        }
        while(!st.isEmpty()){
        temp.append(st.pop());
        }
        temp.reverse();
        sb.append(temp);
        return sb.toString();
    }
}
```
