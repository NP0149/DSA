[Problem Link](https://leetcode.com/problems/reverse-integer/)


```
class Solution {
    boolean check(long sum){
        if(sum>Integer.MAX_VALUE || sum<Integer.MIN_VALUE){
            return true;
        }
        return false;
    }
    public int reverse(int x) {
        int sign=1;
        if(x<0){
            sign=-1;
        }
        long n=Math.abs((long)x);
        long sum=0;
        while(n!=0){
           long rem=n%10;
           sum*=10;
           sum+=rem;
           if(check(sum)){
            return 0;
           }
            n=n/10;
        }
        return (int)sum*sign;
    }
}
```
