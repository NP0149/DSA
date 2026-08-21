# after selling stock cool it down for one day 

```
class Solution {
    static int find(int arr[],int indx,int buy){
        if(indx>=arr.length){
            return 0;
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0)-arr[indx];
            int nottake=find(arr,indx+1,1);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+2,1)+arr[indx];
            int nottake=find(arr,indx+1,0);
            profit=Math.max(take,nottake);
        }
        return profit;
    }
    public int maxProfit(int[] arr) {
        return find(arr,0,1);
    }
}
```
