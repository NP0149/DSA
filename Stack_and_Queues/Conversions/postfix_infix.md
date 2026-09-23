```
import java.util.*;

public class postfix_infix {

    public static void main(String args[]){
        String postfix="AB-DE+F*/";
        int i=0;
        Stack<String> st=new Stack<>();
        while(i<postfix.length()){
            char ch=postfix.charAt(i);
            if(ch>='A' && ch<='Z'){
                String s=Character.toString(ch);
                st.push(s);
            }
            else{
             String b=st.pop();
             String a=st.pop();
             String newone="("+a+ch+b+")";
             st.push(newone);
            }
            i++;
        }
        StringBuilder sb=new StringBuilder();
        while(!st.isEmpty()){
            sb.append(st.pop());
        }
        System.out.println(sb);
    }
}
```
