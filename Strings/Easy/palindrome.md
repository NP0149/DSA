# Check whether the number is palindrome or not 

[Problem Link](https://leetcode.com/problems/palindrome-number/)

# Approach-I

```
class Solution {
    public boolean isPalindrome(int x) {
        String s=Integer.toString(Math.abs(x));
        String s1=new StringBuilder(s).reverse().toString();
        try{
        int num=Integer.parseInt(s1);
        if(num==x){
            return true;
        }
        }catch(Exception e){
            
        }
        return false;
    }
}
```

# complexities

Time:O(1);

space:O(1);

# Approach-II

```
class Solution {
    public boolean isPalindrome(int n) {
        if(n<0){
            return false;
        }
        else{
            int r=0;
            int pal=n;
            while(n!=0){
                int rem=n%10;
                r=r*10+rem;
                n=n/10;
            }
            if(pal==r){
                return true;
            }
            else{
                return false;
            }
        }
    }}
```

# Time complexities

time:O(1);

Space:O(1);
