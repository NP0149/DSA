# Grid Path

## Usual method

```
class Solution {
    static int pathcount(int m,int n){
         if(m<0 || n<0){
            return 0;
        }
        if(m==0 && n==0){
            return 1;
        }
        int right=pathcount(m-1,n);
        int down=pathcount(m,n-1);
        return right+down;
    }
    public int uniquePaths(int m, int n) {
       return pathcount(m-1,n-1);
    }
}
```

## Complexity Analysis

Time:O(2^(m+n))

Space:O(m+n)
