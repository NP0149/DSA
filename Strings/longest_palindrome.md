[Problem Link](https://leetcode.com/problems/longest-palindromic-substring/)

## by standing at every index expand through the index until the characters are equal to one another

## for odd consider the same index for left and right but for even index consider left=i and right=i+1

```
class Solution {
    public String longestPalindrome(String s) {
        int start=0;
        int maxlen=Integer.MIN_VALUE;
        int n=s.length();
        for(int i=0;i<s.length();i++){
            int left=i;
            int right=i;
            while(left>=0 && right<s.length() && s.charAt(left)==s.charAt(right)){
                if(right-left+1>maxlen){
                    start=left;
                    maxlen=right-left+1;
                }
                left--;
                right++;
            }
            left=i;
            right=i+1;

            while(left>=0 && right<n && s.charAt(left)==s.charAt(right)){
                if(right-left+1>maxlen){
                    start=left;
                    maxlen=right-left+1;
                }
                left--;
                right++;
            }
        }
     return s.substring(start,start+maxlen);
    }
}
```
