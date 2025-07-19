# Valid Palindrome

[Problem Link](https://leetcode.com/problems/valid-palindrome/description/?envType=study-plan-v2&envId=top-interview-150)


# Approach-I

1) Two pointer Approach

```
class Solution {
    public boolean isPalindrome(String s) {
        String c=(s.replaceAll("[^a-zA-Z0-9]",""));
           c=c.toLowerCase();
        int n=c.length();
        int i=0;
        int j=n-1;
        if(n==1){
            return true;
        }
        if(n==2){
            if(c.charAt(0)!=c.charAt(1)){
                 return false;
            }
        }
      while(i<j){
         if(c.charAt(i)!=c.charAt(j)){
            return false;
         }
         i++;
         j--;
      }
      return true;
    }
}
```

# Complexities

Time:O(N);
Space:O(1);

# Approach-II

```
class Solution {
    public static boolean isalphanum(char c){
        if((c>='0' && c<='9') || (Character.toLowerCase(c)>='a' && Character.toLowerCase(c)<='z')){
            return true;
        }
        else{
            return false;
        }
    }
    public boolean isPalindrome(String s) {
        int st=0;
        int end=s.length()-1;
        while(st<end){
            if(!isalphanum(s.charAt(st))){
                st++;
                continue;
            }
            if(!isalphanum(s.charAt(end))){
                end--;
                continue;
            }
            if(Character.toLowerCase(s.charAt(st)) != Character.toLowerCase(s.charAt(end))){
                return false;
            }
            st++;
            end--;
        }
         return true;
    }
}
```
# Complexities

Time:O(n)

Space:O(1)
