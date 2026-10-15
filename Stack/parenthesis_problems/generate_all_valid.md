# generate all valid parenthesis string with n pairs of strings

[Problem Link](https://leetcode.com/problems/generate-parentheses/description/?envType=daily-question&envId=2026-10-02)

## every time add opening parenthesis and closing parenthesis every time like if u have reached the limit 2*n check the validity and then add to ans list


```
class Solution {
    boolean isvalid(String s){
        int count=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='('){
                count++;
            }
            else{
                count--;
            }
            if(count<0){
                return false;
            }
        }
        return count==0;
    }
    void generate(List<String> li,int n,StringBuilder sb){
        if(sb.length()==2*n){
            if(isvalid(sb.toString())){
                li.add(sb.toString());
            }
            return;
        }
        sb.append('(');
        generate(li,n,sb);
        
        sb.deleteCharAt(sb.length()-1);

        sb.append(')');
        generate(li,n,sb);

        sb.deleteCharAt(sb.length()-1);
        return;
    }
    public List<String> generateParenthesis(int n) {
        List<String> li=new ArrayList<>();
        StringBuilder sb=new StringBuilder();
        generate(li,n,sb);

        return li;
    }

}
```
