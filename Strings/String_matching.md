
# three characters adjacent to each other should be same,count need to be increased other wise it will be 0

```
import java.util.*;

public class counting {
    public static void main(String args[]){
        String s="BBBBAAAAABBBBBBB";
        int ans=0;
        int count=0;
        int i=0;
        while(i<s.length()){
            if(i+1<s.length() && i+2<s.length() && s.charAt(i)==s.charAt(i+1) &&
                    s.charAt(i+1)==s.charAt(i+2)){
                count=1;
                i=i+3;
            }
            else{
                i=i+1;
                count=0;
            }
            ans+=count;
        }
        System.out.println(ans);
    }

}
```
