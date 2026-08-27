# Number of connected components


```
class dsu{
    private int[]rank;
    public int[]parent;
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
    int countConnected(int v, ArrayList<ArrayList<Integer>> arr) {
       dsu d=new dsu(v);
       for(int i=0;i<arr.size();i++){
           int x=arr.get(i).get(0);
           int y=arr.get(i).get(1);
          d.union(x,y);
       }
       HashSet<Integer> hs=new HashSet<>();
       for(int i=0;i<v;i++){
           hs.add(d.find(i));
       }
       return hs.size();
    }
}
```
