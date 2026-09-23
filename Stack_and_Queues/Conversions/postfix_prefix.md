```
import java.util.*;

public class postfix_prefix {

    public static void main(String args[]){
        String postfix="AB-DE+F*/";
        Stack<String> st=new Stack<>();
        int i=0;
        while(i<postfix.length()){
            char ch=postfix.charAt(i);
            if(ch>='A' && ch<='Z'){
                String newone=Character.toString(ch);
                st.push(newone);
            }
            else{
                String b=st.pop();
                String a=st.pop();
                String s=ch+a+b;
                st.push(s);
            }
       i++;
        }
        StringBuilder sb=new StringBuilder();
        while(!st.isEmpty()){
            sb.append(st.pop());
        }
        System.out.println(sb.toString());
    }

}
```
