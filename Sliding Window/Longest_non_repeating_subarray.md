# Longest substring with no repeating characters

[Problem Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

# Approach-I

1)first we need to add elements which doesnot repeat in the array previously and then if there is any character that is repeated then we need
iterate in while loop by removing character at l,and then we need to add it and then need to check the max length and need to update it

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> hs=new HashSet<>();
        int l=0;
        int ans=-1;
        for(int i=0;i<s.length();i++){
          char ch=s.charAt(i);
          if(!hs.contains(ch)){
            hs.add(ch);
          }
         else{
            while(hs.contains(ch)){
                hs.remove(s.charAt(l));
                l++;
            }
            hs.add(ch);
         }
         ans=Math.max(ans,i-l+1);
        }
        return ans;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)
