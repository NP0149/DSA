# Longest Repeating Character

[Problem Link](https://leetcode.com/problems/longest-repeating-character-replacement/submissions/1707163133/)

# Approach-I

1)need to consider a array and then we need to store the individual character count ,everytime we need to compare the current freq with the 
max frequency and then size of sliding window also,if size of window- maxfreq>k,then we need to remove the character at l place
and then increase the l value

```
class Solution {
    public int characterReplacement(String s, int k) {
        int count[]=new int[26];
        int  maxfreq=0;
        int l=0;
        int ans=0;
        for(int i=0;i<s.length();i++){
            count[s.charAt(i)-'A']++;
          maxfreq=Math.max(maxfreq,count[s.charAt(i)-'A']);
          while((i-l+1)-maxfreq >k){
            count[s.charAt(l)-'A']--;
            l++;
          }
          ans=Math.max(ans,i-l+1);
        }
        return ans;
    }
}
```
# Complexities

Time:O(n)

Space:O(n)
