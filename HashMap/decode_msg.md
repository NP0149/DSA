# decoding the message

[Problem Link](https://leetcode.com/problems/decode-the-message/description/)


# Approach

1)assign one value to one character,if any of characters repeated then just skip that by this a table will be created from then 
decode the message given

```
class Solution {
    public static String decodeMessage(String key, String message) {
        HashMap<Character,Character> map=new HashMap<>();
        int i=0;
        String key1=key.replaceAll(" ","");
        String decode="";
        for(char ch:key1.toCharArray()){
            if(!map.containsKey(ch)){
                map.put(ch,(char)(97+i));
                i++;
            }
        }
        for(char ch:message.toCharArray()){
            if(map.containsKey(ch)){
               decode+=map.get(ch);
            }
            else{
                decode+=ch;
            }
        }
        return decode;
    }
}

```

# complexities

Time:O(nlogn);

spcae:O(1);
