# You can buy stock only after selling and this should be done in 2 caps

# recurrsion

```
class Solution {
    static int find(int arr[],int indx,int buy,int cap){
        if(cap==0){
            return 0;
        }
        if(indx==arr.length){
            return 0;
        }
        int profit=0;
        if(buy==1){
            int take=find(arr,indx+1,0,cap)-arr[indx];
            int nottake=find(arr,indx+1,1,cap);
            profit=Math.max(take,nottake);
        }
        else{
            int take=find(arr,indx+1,1,cap-1)+arr[indx];
            int nottake=find(arr,indx+1,0,cap);
            profit=Math.max(take,nottake);
        }
        return profit;
    }
    public int maxProfit(int[] arr) {
        int cap=2;
        return find(arr,0,1,cap);
    }
}
```
