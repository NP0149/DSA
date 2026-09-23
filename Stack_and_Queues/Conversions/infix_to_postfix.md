```
import java.util.*;

public class infixtopostfix {
   static int getprecedence(char ch){
       if(ch=='^'){
           return 4;
       }
       else if(ch=='*' || ch=='/'){
           return 3;
       }
       else if(ch=='+' || ch=='-'){
           return 2;
       }
       return 0;
   }

    static String find(String infix){
        Stack<Character> st=new Stack<>();
        int i=0;
        StringBuilder sb=new StringBuilder();
        while(i<infix.length()){
            char ch=infix.charAt(i);
            if((ch>='A' && ch<='Z') || (ch>='a' && ch<='z') || (ch>='0' && ch<='9')){
                sb.append(ch);
            }
            else if(ch=='('){
                st.push(ch);
            }
           else if(ch==')'){
               while(!st.isEmpty() && st.peek()!='('){
                   sb.append(st.pop());
               }
               st.pop();
            }
           else{
               if(!st.isEmpty() && getprecedence(st.peek())>=getprecedence(ch)){
                   while( !st.isEmpty() && getprecedence(st.peek())>getprecedence(ch) || (getprecedence(st.peek())==getprecedence(ch) && st.peek()!='^')){
                       sb.append(st.pop());
                   }
               }
             st.push(ch);
            }
            i++;
        }
        while(!st.isEmpty()){
            sb.append(st.pop());
        }
        return sb.toString();
    }

    public static void main(String args[]){
        String infix="A^B^C";
        String postfix=find(infix);
        System.out.println(infix+"=="+postfix);
    }
}
```
