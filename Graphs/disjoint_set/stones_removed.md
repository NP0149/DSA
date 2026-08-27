# number of stones those are need to be removed

```

class dsu{
    private int[]rank;
    public int []parent;
    dsu(int v){
        rank=new int[v];
        parent=new int[v];
        for(int i=0;i<v;i++){
            rank[i]=0;
            parent[i]=i;
        }
    }
    public int find(int node){
        if(parent[node]!=node){
            return parent[node]=find(parent[node]);
        }
        return parent[node];
    }
    public void union(int x,int y){
        int p1=find(x);
        int p2=find(y);
        if(p1!=p2){
            if(rank[p1]>rank[p2]){
                parent[p2]=p1;
            }
            else if(rank[p1]<rank[p2]){
                parent[p1]=p2;
            }
            else{
                parent[p2]=p1;
                rank[p1]++;
            }
        }
    }
}

class Solution {
    public int removeStones(int[][] arr) {
        int max_row=0;
        int max_col=0;
        for(int i=0;i<arr.length;i++){
            max_row=Math.max(max_row,arr[i][0]);
            max_col=Math.max(max_col,arr[i][1]);
        }
        dsu d=new dsu(max_row+max_col+2);
       for(int a[]:arr){
        int row=a[0];
        int col=max_row+a[1]+1;
        if(d.find(row)!=d.find(col)){
            d.union(row,col);
        }
       }
       int count=0;
       int v=max_row+max_col+2;
       HashMap<Integer,Integer> hm=new HashMap<>();
       for(int i=0;i<v;i++){
        hm.put(d.find(i),hm.getOrDefault(d.find(i),0)+1);
       }
       for(int num:hm.keySet()){
        if(hm.get(num)>1){
            count++;
        }
       }
       return arr.length-count;
    }
}
```
