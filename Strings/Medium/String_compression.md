# String compression

[Problem Link](https://leetcode.com/problems/string-compression/submissions/1704455242/)

# Approach-I

```
class Solution {
    public int compress(char[] chars) {
        String s="";
        int i=0;
        int idx=0;
        while(i<chars.length){
            char c=chars[i];
            int count=0;
            while(i<chars.length && chars[i]==c){
                i++;
                count++;
            }
           chars[idx++]=c;
           if(count>1){
            String str=Integer.toString(count);
            for(char dig : str.toCharArray()){
            chars[idx++]=dig;
            }
           }
        }
       return idx;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
