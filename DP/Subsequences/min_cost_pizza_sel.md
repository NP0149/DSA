# Min cost pizza selection
[Problem Link](https://www.geeksforgeeks.org/problems/pizza-mania0155/1)

```
class Solution {
    static int min_cost;
    void find(int area[],int cost[],int indx,int target,int costing){
         if(target<=0){
            if(costing<min_cost){
                min_cost=costing;
            }
          return;
        }
        if(indx>=area.length){
            return;
        }
       find(area,cost,indx+1,target,costing);
        find(area,cost,indx,target-area[indx],costing+cost[indx]);
    }
    public int minimumCost(int x, int s, int m, int l, int cs, int cm, int cl) {
        // code here
        int area[]=new int[3];
        int cost[]=new int[3];
        area[0]=s;
        area[1]=m;
        area[2]=l;
        cost[0]=cs;
        cost[1]=cm;
        cost[2]=cl;
        min_cost=Integer.MAX_VALUE;
        find(area,cost,0,x,0);
        return min_cost;
        
    }
}
```
