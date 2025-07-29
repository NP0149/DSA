# Maximum depth of parenthesis

[Problem Link](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)


# Approach-I

1) if char '(' encountered then ans++,if char ')' encountered then ans--

```
class Solution {
    public int maxDepth(String s) {
        int ans=0;
        int maxans=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
           if(ch=='('){
           ans++;
           maxans=Math.max(maxans,ans);
           }
           else if(ch==')'){
            ans--;
           }
        }    
        return maxans;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)

# Approach-II

using stack if  char '(' encountered just push into stack if ')' pop from stack

ans will max of stack size and ans

```
class Solution {
    public int maxDepth(String s) {
        Stack<Character> st=new Stack<>();
        int ans=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
           if(ch=='('){
            st.push(ch);
           }
           else if(ch==')'){
            st.pop();
           }
            ans=Math.max(ans,st.size());
        }    
        return ans;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
