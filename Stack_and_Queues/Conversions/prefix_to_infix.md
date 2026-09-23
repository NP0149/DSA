```
import java.util.*;

public class prefix_infix {

    public static void main(String args[]){
        String prefix="+*-abc";
        Stack<String> st=new Stack<>();
        int i=prefix.length()-1;
        while(i>=0){
            char ch=prefix.charAt(i);
            if(ch>='a' && ch<='z'){
                String newone=Character.toString(ch);
                st.push(newone);
            }
            else{
                String b=st.pop();
                String a=st.pop();
                String s="("+a+ch+b+")";
                st.push(s);
            }
            i--;
        }
        StringBuilder sb=new StringBuilder();
        while(!st.isEmpty()){
            sb.append(st.pop());
        }
        System.out.println(sb.toString());
    }

}
```
