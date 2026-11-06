[Problem Link](https://leetcode.com/problems/zigzag-conversion/)


```
class Solution {
    public String convert(String s, int n) {
         if(n==1 || n>=s.length()){
            return s;         
            }
            StringBuilder rows[]=new StringBuilder[n];
      for(int i=0;i<n;i++){
        rows[i]=new StringBuilder();
      }
      int row=0;
      int dir=1;
      for(int i=0;i<s.length();i++){
        rows[row].append(s.charAt(i));
        if(row==0){
            dir=1;
        }
        else if(row==n-1){
            dir=-1;
        }
        row+=dir;
      }
      StringBuilder sb=new StringBuilder();
      for(int i=0;i<n;i++){
         sb.append(rows[i].toString());
      }
      return sb.toString();
    }
}
```
