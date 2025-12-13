# Remove k digits

[Problem Link](https://leetcode.com/problems/remove-k-digits/)

# Brute (But doesnot work for all testcases)

```
class Solution {
    public String removeKdigits(String s, int k) {
        int n=s.length();
        Long mini=Long.MAX_VALUE;
        if(s.length()==k){
            return "0";
        }
   for(int i=0;i<=n-k;i++){
    String sb=s.substring(0,i)+s.substring(i+k);
    if(sb.length()==0){
        continue;
    }
    Long a=Long.parseLong(sb);
     mini=Math.min(mini,a);
   }
   String l=Long.toString(mini);
   return l;
     }
}
```

# Complexity Analysis

Time:O(n^2)

Space:O(n)

# Optimal Approach

```
class Solution {
    public String removeKdigits(String s, int k) {
        Stack<Integer> st=new Stack<>();
        if(s.length()==k){
            return "0";
        }
        for(int i=0;i<s.length();i++){
            int num=s.charAt(i)-'0';
            while(!st.isEmpty() && st.peek()>num && k>0){
                st.pop();
                k--;
            }
          st.push(num);
        }
        while(k>0 && !st.isEmpty()){
            st.pop();
            k--;
        }
      StringBuilder sb=new StringBuilder();
      while(!st.isEmpty()){
        sb.append(st.pop());
      }
      sb.reverse();
       int idx=0;
       while(idx<sb.length()-1 && sb.charAt(idx)=='0'){
        idx++;
       }
       sb.delete(0,idx);
       return sb.length()==0?"0":sb.toString();
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
