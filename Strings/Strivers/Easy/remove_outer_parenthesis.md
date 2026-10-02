[Problem Link](https://leetcode.com/problems/remove-outermost-parentheses/submissions/2159786213/)

### if count==0 if ch=='(' ,here increase the count after adding the character,it is the outermost 
### so we should not add it to the result and if count>1 and ch==')' then it is the outermost ,decrease the count after adding it

```
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder sb=new StringBuilder();
        int count=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='(' && count>0){
                sb.append(ch);
                count++;
            }
            else if(ch==')' && count>1){
                sb.append(ch);
                count--;
            }
            else if(ch=='('){
                count++;
            }
            else{
                count--;
            }
        }
        return sb.toString();
    }
}
```
