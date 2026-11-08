[Problem Link](https://leetcode.com/problems/powx-n/)


```
class Solution {
    double find(double x,int n){
        long num=n;
        if(n<0){
         num=-num;
        }
        double ans=1;
        while(num!=0){
            if(num%2==1){
              ans*=x;
            }
            x=x*x;
            num=num/2;
        }
        if(n<0){
            ans=1/ans;
        }
        return ans;
    }
    public double myPow(double x, int n) {
        return find(x,n);
    }
}
```
