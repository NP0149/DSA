# best time to sell to stocks and buy stocks

[problem link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/?envType=study-plan-v2&envId=top-interview-150)

```
 class Solution {
    public int maxProfit(int[] prices) {
        int n=prices.length;
        int temp=0;
        int profit=0;
        int low=100000;
        for(int i=0;i<n;i++){
            temp=prices[i]-low;
            profit=Math.max(profit,temp);
            if(prices[i]<low)
            low=prices[i];
        }
        return profit;
    }
}
```
