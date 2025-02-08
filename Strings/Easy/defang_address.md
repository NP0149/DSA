# Defang address
[Problem link](https://leetcode.com/problems/defanging-an-ip-address/)

# Approach I

1) iterate through all the characters of a string replace character "." with "[.]",then you will obtain defang address
```Java
class Solution {
    public String defangIPaddr(String address) {
        String ans="";
        for(int i=0;i<address.length();i++){
            char ch=address.charAt(i);
            if(ch=='.'){
             ans=ans+"[.]";
            }
            else{
                ans=ans+ch;
            }
        }
        return ans;
    }
}
```
# Approach-II
1)by using string functions just replace '.' character with "."

```Java
class Solution {
    public String defangIPaddr(String address) {
        return address.replace(".","[.]");

    }
```
# Complexity
time complexity:O(N)
