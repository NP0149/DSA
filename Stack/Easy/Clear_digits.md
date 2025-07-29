# Clear Digits

[Problem Link](https://leetcode.com/problems/clear-digits/)

# Approach-I

```
class Solution {
    public String clearDigits(String s) {
        Stack<Character> st=new Stack<>();
        StringBuilder sb=new StringBuilder();
       for(int i=0;i<s.length();i++){
        char ch=s.charAt(i);
        st.push(ch);
        if(Character.isDigit(st.peek())){
            st.pop();
            st.pop();
        }
       }
      while(!st.isEmpty()){
       sb.append(st.pop());
      }
      return sb.reverse().toString();
        }
    }
```

# Complexity Analysis

Time:O(n)

Space:O(n)
