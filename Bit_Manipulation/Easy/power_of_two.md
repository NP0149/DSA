# Power of 2
[Problem Link](https://leetcode.com/problems/power-of-two/)


# Approach-I(Better)

1)leetcode is not considering negative numbers as even so first put that edge case and then do iterative right shift

2)n>>1=n%2

3)n&1 means checking the right most bit

```
class Solution {
    public boolean isPowerOfTwo(int n) {
      int count=0;
      if(n<0){
       return false;
      }
      while(n!=0){
        if((n&1)==1){
            count++;
        }
        n=n>>1;
      }
      if(count==1){
        return true;
      }
      return false;
}
}
```

# Complexities

Time:O(log n)

Space:O(1)


# Approach-II(Best)

1)definitely n>0 and n&(n-1)==0

```
class Solution {
    public boolean isPowerOfTwo(int n) {
     return n>0 && (n&(n-1))==0;
    }
}
```
# Complexities

Time:O(1)

Space:O(1)
