```
import java.util.*;


public class prefix_postfix {

    public static void main(String args[]){
        String prefix="/-AB*+DEF";
       int i=prefix.length()-1;
       Stack<String> st=new Stack<>();
       while(i>=0){
           char ch=prefix.charAt(i);
           if(ch>='A' && ch<='Z'){
               String newone=Character.toString(ch);
               st.push(newone);
           }
           else{
               String b=st.pop();
               String a=st.pop();
               String s=b+a+ch;
               st.push(s);
           }
           i--;
       }
        System.out.println(st.peek());
    }

}
```
