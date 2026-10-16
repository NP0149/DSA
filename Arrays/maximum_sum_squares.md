# maximize sum of squares

[Problem Link](https://leetcode.com/problems/maximize-sum-of-squares-of-digits/?envType=daily-question&envId=2026-10-14)


```
class Solution {
    public String maxSumOfSquares(int num, int sum) {
        StringBuilder sb=new StringBuilder();
        int max=9*num;
        if(sum>max){
            return sb.toString();
        }
        for(int i=0;i<num;i++){
          if(sum>=9){
            sum-=9;
            sb.append('9');
          }
          else{
                char ch=(char)(sum+'0');
            sb.append(ch);
            sum=0;
          }
        }
        return sb.toString();
    }
}
```
