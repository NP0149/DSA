# Valid Anagram

[Problem Link](https://leetcode.com/problems/valid-anagram/description/)
# Approach-I

anagram means that occurance(frequency) of the letters in a word should be same,it is case sensitive also...


```
class Solution {
    public boolean isAnagram(String s, String t) {
       HashMap<Character,Integer> hm=new HashMap<>();
        HashMap<Character,Integer> hm1=new HashMap<>();
        for(int i=0;i<s.length();i++){
            if(hm.containsKey(s.charAt(i))){
                int prev=hm.get(s.charAt(i));
                hm.put(s.charAt(i),prev+1);
            }
            else{
                hm.put(s.charAt(i),1);
            }
        }
        for(int i=0;i<t.length();i++){
            if(hm1.containsKey(t.charAt(i))){
                int prev=hm1.get(t.charAt(i));
                hm1.put(t.charAt(i),prev+1);
            }
            else{
                hm1.put(t.charAt(i),1);
            }
        }
        if(hm.equals(hm1)){
            return true;
        }
return false;
    }
    }
```


# Complexities


Time:O(n);// the length of the string

Space:O(1);


# Approach-II


1)consider two strings as arrays then sort those arrays check whether the arrays are equal or not


```

class Solution {
    public boolean isAnagram(String s, String t) {
        char[] schars=s.toCharArray();
        char[] tchars=t.toCharArray();

        Arrays.sort(schars);
        Arrays.sort(tchars);

        return  Arrays.equals(schars,tchars);
    }}

```
# complexities


Time:O(nlogn)//n is the length of the string and its time complexity because of sorting

Space:O(n);//string length
