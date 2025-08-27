# XOR from left to right

# Approach-I

1)finding xor will be according to some pattern that we can follow a method that we need to find m=number%4

2)if m==0,then return number if m==1 return 1,if m==2 return number+1,if m==3 return 0

        3)at last return xor(l-1)^xor(r)

```
class Solution {
    static int find(int l){
        int m=l%4;
        if(m==0){
            return m;
        }
        else if(m==1){
            return 1;
        }
        else if(m==2){
            return l+1;
        }
        else if(m==3){
            return 0;
        }
        else{

        }
        return -1;
    }
    public int findRangeXOR(int l, int r) {
        return find(l-1)^find(r);

    }
}
```
 # Complexity Analysis

Time:O(1)

Space:O(1)
