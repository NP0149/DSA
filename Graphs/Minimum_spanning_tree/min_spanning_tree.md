# Minimum spanning tree

```

         
class pair{
    int node;
    int parent;
    int wt;
    pair(int node,int parent,int wt){
        this.node=node;
        this.parent=parent;
        this.wt=wt;
    }
}


class Solution {
    public int spanningTree(int V, int[][] arr) {
        List<List<pair>> li=new ArrayList<>();
        for(int i=0;i<V;i++){
            li.add(new ArrayList<pair>());
        }
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v=arr[i][1];
            int wt=arr[i][2];
            li.get(v).add(new pair(u,v,wt));
            li.get(u).add(new pair(v,u,wt));
        }
        int visited[]=new int[V];
      PriorityQueue<pair> pq=new PriorityQueue<>((a,b)->a.wt-b.wt);
      pq.add(new pair(0,-1,0));
       int mst=0;
      while(!pq.isEmpty()){
          pair p=pq.poll();
          int node=p.node;
          int parent=p.parent;
          int wt=p.wt;
          if(visited[node]==1){
              continue;
          }
          visited[node]=1;
             mst+=wt;
          for(pair top:li.get(node)){
              if(visited[top.node]!=1){
              pq.add(new pair(top.node,node,top.wt));
              }
          }
      }
      return mst;
        
    }
}
```
