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

Two pointer approach

```
public class validPal {
    public static boolean valid(String s){
        String a=s.toLowerCase();
        String s1=a.replaceAll("[^A-Za-z0-9]","");
        int n=s1.length();
        int i=0;
        int j=n-1;
        while(i<j){
           if(s1.charAt(i)!=s1.charAt(j)) {
               return false;
           }

           i++;
           j--;
        }
           return true;
        }
    public static void main(String args[]){
        String s="A man, a plan, a canal: Panama";
       boolean a=valid(s);
       System.out.println(a);
    }

}

```

# complexities

Time:O(n);

Space:O(n);
