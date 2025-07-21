# Fruits into Basket

[Problem Link](https://leetcode.com/problems/fruit-into-baskets/description/)

# Approach-I

1)the basket should only contain k number of items ,if one basket is filled with one type other type should not be filled in the basket
so we need to calculate max number of fruits we can take from the basket

```
class Solution {
    public int totalFruit(int[] fruits) {
        int n=fruits.length;
        int l=0;
        int ans=0;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<n;i++){
            int val=fruits[i];
            hm.put(val,hm.getOrDefault(val,0)+1);
            while(hm.size()>2){
                int lval=fruits[l];
                hm.put(lval,hm.get(lval)-1);
                if(hm.get(lval)==0){
                    hm.remove(lval);
                }
                l++;
            }
          ans=Math.max(ans,i-l+1);
        }
        return ans;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)
