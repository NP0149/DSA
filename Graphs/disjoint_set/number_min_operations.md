# Minimum number of operations required 


```
class dsu{
    private int[]rank;
    public int[] parent;
    dsu(int v){
        rank=new int[v];
        parent=new int[v];
        for(int i=0;i<v;i++){
            parent[i]=i;
            rank[i]=0;
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
                parent[p1]=p2;
                rank[p2]++;
            }
        }
    }
}
class Solution {
    public int makeConnected(int n, int[][] arr) {
        dsu d=new dsu(n);
        int extra=0;
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v=arr[i][1];
            if(d.find(u)!=d.find(v)){
                d.union(u,v);
            }
            else{
                extra++;
            }
        }
        int count=0;
        for(int i=0;i<n;i++){
            if(d.parent[i]==i){
                 count++;
            }
        }
        int req=count-1;
        if(extra>=req){
            return req;
        }
        return -1;
    }
}

```
