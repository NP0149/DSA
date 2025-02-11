# Best time to sell stocks

[Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

# Approach I (BRUTE FORCE)

traverse the array two times and then find the max value from j loop the find the difference
between max value and the i loop array member and then find the max difference 
from array and then return the max difference value

```Java
class solution{
 public int findmaxprofit(int arr[]){
 int n=arr.length;
 int max=-1;
 int temp=-1;
 for(int i=0;i<n;i++){
 for(int j=i+1;j<n;j++){
   if(max<arr[j]){
  max=arr[j];
  }
  int diff=max-arr[i];
  temp=Math.max(temp,diff);
  }
  }
  return temp;
  }
```
# Aproach II

consider the element in the right and then find the minimum value from the rest of left array 
and then find the difference store it in temp,if profit value less than temp then make profit equals to temp
and then return the profit

```Java
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

# Complexity Analysis

Time complexity:O(N^2) for Brute force

time complexity:O(N) for Approach II
