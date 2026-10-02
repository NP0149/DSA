[Problem Link](https://leetcode.com/problems/longest-common-prefix/)


```
class Solution {
    public String longestCommonPrefix(String[] str) {
       
        Arrays.sort(str);
         String first=str[0];
        String last=str[str.length-1];
        StringBuilder sb=new StringBuilder();
        for(int i=0;i<first.length();i++){
            if(first.charAt(i)==last.charAt(i)){
                sb.append(first.charAt(i));
            }
            else{
                break;
            }
        }
        return sb.toString();
    }
}
```
