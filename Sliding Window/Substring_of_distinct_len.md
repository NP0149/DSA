# Substring of distinct length

[Problem Link](https://leetcode.com/problems/substrings-of-size-three-with-distinct-characters/)

# Approach 

1)generate all the substrings 

2)sepearte substrings which have length 3

3)consider a hashset,add elements into it which are not repeating earlier so if the hashset size matches the substring length
then increase the count and at last return the count

```
class Solution {
    public int countGoodSubstrings(String s) {
         int n = s.length();
        int sl = 3;
        int count = 0;
        for (int i = 0; i < n - sl + 1; i++) {
            int j = i + sl - 1;
            String m = "";
            for (int k = i; k <= j; k++) {
                m += s.charAt(k);
            }
           if(m.length()==sl){
                HashSet<Character> ch=new HashSet<>();
                for(int t=0;t<sl;t++){
                  if(!ch.contains(m.charAt(t))){
                      ch.add(m.charAt(t));
                  }
               }
               if(ch.size()==sl){
                 count++;
               }
           }
       }
       return count;
    }
    }

```

# Complexity Analysis

Time:O(N);

Space:O(1);
