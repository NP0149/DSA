# Fractional Knapsack

[Problem Link](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)


```class Solution {
    static class Item{
        int value,weight;
        Item(int val,int wt){
            value=val;
            weight=wt;
        }
    }
    public double fractionalKnapsack(int[] val, int[] wt, int capacity) {
        // code here
        Item items[]=new Item[val.length];
        for(int i=0;i<val.length;i++){
            items[i]=new Item(val[i],wt[i]);
        }
        Arrays.sort(items,(a,b)->Double.compare((double)b.value/b.weight,(double)a.value/a.weight));
        double ans=0;
        for(Item it:items){
            if(capacity>=it.weight){
                ans+=it.value;
                capacity-=it.weight;
            }
            else{
                double k=((double)it.value/it.weight)*capacity;
                ans+=k;
                break;
            }
        }
        return ans;
    }
}
```

# Complexity Analysis

Time:O(nlogn)

Space:O(n)
