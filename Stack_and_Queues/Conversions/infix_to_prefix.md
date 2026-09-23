```
import java.util.*;

public class infix_prefix{
    static int precedence(char ch){
        if(ch=='^'){
            return 3;
        }
        else if(ch=='+' || ch=='-'){
            return 1;
        }
        else if(ch=='*' || ch=='/'){
            return 2;
        }
        return 0;
    }

    static String find(String infix){
        StringBuilder s=new StringBuilder();
        for(int i=0;i<infix.length();i++){
            if(infix.charAt(i)==')'){
              s.append('(');
            }
            else if(infix.charAt(i)=='('){
                s.append(')');
            }
            else{
                s.append(infix.charAt(i));
            }
        }
        StringBuilder sb=new StringBuilder();
        int i=0;
        Stack<Character> st=new Stack<>();
        while(i<s.length()){
            if(s.charAt(i)>='a' && s.charAt(i)<='z'){
                sb.append(s.charAt(i));
            }
            else if(s.charAt(i)=='('){
                st.push(s.charAt(i));
            }
            else if(s.charAt(i)==')'){
                while(!st.isEmpty() && st.peek()!='('){
                    st.pop();
                }
                st.pop();
            }
            else{
                if(s.charAt(i)=='^'){
                    while(!st.isEmpty() && precedence(st.peek())<=precedence(s.charAt(i))){
                        sb.append(st.pop());
                    }
                }
                else {
                    while(!st.isEmpty() && precedence(st.peek())<precedence(s.charAt(i))){
                        sb.append(st.pop());
                    }
                    st.push(s.charAt(i));
                }
            }
            i++;
        }
        while(!st.isEmpty()){
            sb.append(st.pop());
        }
        return sb.reverse().toString();
    }
    public static void main(String args[]){
        String infix="a+b-c";
        String prefix=find(infix);
        System.out.println(prefix);
    }
}
```
