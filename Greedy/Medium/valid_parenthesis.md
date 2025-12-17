# Valid Parenthesis

[Problem Link](https://leetcode.com/problems/valid-parenthesis-string/submissions/1858265920/)


```
class Solution {
    public boolean checkValidString(String s) {
        int mincount=0;
        int maxcount=0;
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='('){
              mincount++;
              maxcount++;
            }
            else if(s.charAt(i)==')'){
                mincount--;
                maxcount--;
            }
            else{
                mincount--;
                maxcount++;
            }
            if(mincount<0){
                mincount=0;
            }
            if(maxcount<0){
                return false;
            }
        }
        return mincount==0;
    }
}
```

# Complexity Analysis

Time:O(n);

Space:O(1)
