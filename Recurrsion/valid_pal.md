# valid palindrome

# Approach-I

```
public class validPal {
    public static boolean valid(String s){
        String a=s.toLowerCase();
        String s1=a.replaceAll("[^A-Za-z0-9]","");
        String s2=new StringBuilder(s1).reverse().toString();
        if(s2.equals(s1)){
            return true;
        }
        return false;
    }
    public static void main(String args[]){
        String s="A man, a plan, a canal: Panama";
       boolean a=valid(s);
       System.out.println(a);
    }

}
```

# Complexities

Time:O(n);

Space:O(n);

# Approach-II

