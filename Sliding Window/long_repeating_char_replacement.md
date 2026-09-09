```
class Solution {
    public int characterReplacement(String s, int k) {
       int freq[]=new int[26];
       int maxfreq=0;
       int maxlen=0;
       int l=0;
       for(int i=0;i<s.length();i++){
         int curr=++freq[s.charAt(i)-'A'];
         maxfreq=Math.max(maxfreq,curr);
         int change=(i-l+1)-maxfreq;
         if(change>k){
            freq[s.charAt(l)-'A']--;
            l++;
         }
         maxlen=Math.max(maxlen,i-l+1);
       }
       return maxlen;
    }
}
```
