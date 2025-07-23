# finding all anagrams in a string

[Problem Link](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)

# Approach-I

```
class Solution {
    public static boolean fun(HashMap<Character,Integer> hms,HashMap<Character,Integer> hmp){
        for(char key:hms.keySet()){
            if(!hmp.containsKey(key)){
                return false;
            }
            int a=hms.get(key);
            int b=hmp.get(key);
            if(a!=b){
                return false;
            }
        }
        return true;
    }
    public List<Integer> findAnagrams(String s, String p) {
        HashMap<Character,Integer> hms=new HashMap<>();
        HashMap<Character,Integer> hmp=new HashMap<>();
        List<Integer> li=new ArrayList<>();
        for(int i=0;i<p.length();i++){
            char ch=p.charAt(i);
            hmp.put(ch,hmp.getOrDefault(ch,0)+1);
        }
        int l=0;
        int k=p.length();
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            hms.put(ch,hms.getOrDefault(ch,0)+1);
            if(i-l==k){
                char lval=s.charAt(l);
                hms.put(lval,hms.get(lval)-1);
                if(hms.get(lval)==0){
                    hms.remove(lval);
                }
                l++;
            }
            if(i-l+1==k){
                if(fun(hms,hmp)){
                  li.add(l);
                }
            }

        }
        return li;
    }
}
```

# Complexities

Time:O(n)

Space:O(n)
