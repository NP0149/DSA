# decode the message II

[Problem Link](https://leetcode.com/problems/isomorphic-strings/description/)

# Approach-I

1)consider two hashmaps store key to value in one hashmap and in another store value to key so if there is an element that was repeated
then check in both the hashmaps whether the assigned value is correct or not

```
class Solution {
    public boolean isIsomorphic(String s, String t) {
        HashMap<Character,Character> hm=new HashMap<>();
           HashMap<Character,Character> rev=new HashMap<>();
           boolean ans=true;
           for(int i=0;i<s.length();i++){
            char ch1=s.charAt(i);
            char ch2=t.charAt(i);
            if(!hm.containsKey(ch1) && !rev.containsKey(ch2)){
                hm.put(ch1,ch2);
                rev.put(ch2,ch1);
            }
            else if(hm.containsKey(ch1) && hm.get(ch1)!=ch2){
                ans=false;
                break;
            }
            else if(rev.containsKey(ch2) && rev.get(ch2)!=ch1){
                ans=false;
                break;
            }
           }
           return ans;
    }
}
```

# Complexities

Time:O(N);

Space:O(N);
