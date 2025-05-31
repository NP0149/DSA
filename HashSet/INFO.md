# HashSet 

1) Mainly used to maintain the uniqueness in the data

```
import java.util.*;
public class hashset {
    public static void main(String args[]){
        HashSet<String> hs=new HashSet<>();
        hs.add("navya");
        hs.add("divya");
        hs.add("mouni");
        hs.add("navya");
        System.out.println(hs.contains("navya"));//true
        System.out.println(hs.size());//3
        hs.remove("divya");
        System.out.println(hs.contains("divya"));//false
        System.out.println(hs.size());//2
    }

}
```
