# reverse bits

[Problem Link](https://leetcode.com/problems/reverse-bits/submissions/1921348640/?envType=daily-question&envId=2026-02-16)

```
class Solution {
    public int reverseBits(int n) {
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<32;i++){
            st.push(n&1);
            n=n>>>1;
        }
        List<Integer> li=new ArrayList<>();
        while(!st.isEmpty()){
            li.add(st.pop());
        }
        int m=0;
        int indx=0;
        for(int i=0;i<li.size();i++){
          m+=(int)Math.pow(2,indx)*li.get(i);
          indx++;
        }
        return m;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
