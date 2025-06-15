# Minimum cost of buying candies with discount

[Problem Link](https://leetcode.com/problems/minimum-cost-of-buying-candies-with-discount/description/)

# Approach-I

1)sort the array and then from last sum 2 and then miss 3 one

```
class Solution {
    public int minimumCost(int[] arr) {
       int n=arr.length;
       int took=0;
       int ans=0;
       Arrays.sort(arr);
       for(int i=n-1;i>=0;i--){
            if(took==2){
                took=0;
            }
            else{
                ans+=arr[i];
                took++;
            }

       }
       return ans;
    }
}
```

# Complexity Analysis

Time:O(N log N);

Space:O(1);

