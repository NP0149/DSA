# Valid Palindrome

[Problem Link](https://leetcode.com/problems/valid-palindrome/description/?envType=study-plan-v2&envId=top-interview-150)


# Approach 

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
