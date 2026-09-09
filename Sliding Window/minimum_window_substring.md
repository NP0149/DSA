[Problem Link](https://leetcode.com/problems/minimum-window-substring/)


```
class Solution {
    boolean compare(HashMap<Character,Integer> hm1,HashMap<Character,Integer> hm2){
        for(char ch:hm2.keySet()){
            if(hm1.get(ch)==null){
                return false;
            }
            else if(hm1.get(ch)<hm2.get(ch)){
                return false;
            }
        }
        return true;
    }
    public String minWindow(String s, String t) {
        HashMap<Character,Integer> hm2=new HashMap<>();
        for(int i=0;i<t.length();i++){
         hm2.put(t.charAt(i),hm2.getOrDefault(t.charAt(i),0)+1);
        }
        int l=0;
        int start=0;
        int minlen=Integer.MAX_VALUE;
        HashMap<Character,Integer> hm1=new HashMap<>();
        for(int i=0;i<s.length();i++){
            hm1.put(s.charAt(i),hm1.getOrDefault(s.charAt(i),0)+1);
            while(compare(hm1,hm2)){
                int len=i-l+1;
                if(len<minlen){
                    minlen=len;
                    start=l;
                }
              int val=hm1.get(s.charAt(l));
              hm1.put(s.charAt(l),val-1);
              if(val-1==0){
                hm1.remove(s.charAt(l));
              }
              l++;
            }
        }
        if(minlen==Integer.MAX_VALUE){
            return "";
        }
        String ans=s.substring(start,start+minlen);
      return ans;
    }
}
```
