# buy and sell stocks II

[Problem Link](m/problems/best-time-to-buy-and-sell-stock-ii/description/?envType=study-plan-v2&envId=top-interview-150)

```
 class Solution {
    public int maxProfit(int[] arr) {
int n=arr.length;
int minidx=0;
int diff=0;
int max=0;
int profit=0;
int min=arr[minidx];
 for(int i=0;i<n-1;i++){
if(arr[i]<arr[minidx] && i>minidx){
 minidx=i;
 min=arr[i];
 }
 diff=arr[i]-arr[minidx];
 max=Math.max(diff,max);
 if(arr[i]<arr[i+1]){
    profit+=arr[i+1]-arr[i];
 }
 max=Math.max(profit,max);
 }
 return max;
 }
        
    }
```
