# using priority Queue


```
class pair{
    int node;
    int wt;
    pair(int node,int wt){
        this.node=node;
        this.wt=wt;
    }
}

class Solution {
    public ArrayList<Integer> dijkstra(int V, int[][] arr, int src) {
      List<List<pair>> li=new ArrayList<>();
      for(int i=0;i<V;i++){
          li.add(new ArrayList<pair>());
      }
      for(int i=0;i<arr.length;i++){
          int u=arr[i][0];
          int v=arr[i][1];
          int wt=arr[i][2];
          li.get(u).add(new pair(v,wt));
          li.get(v).add(new pair(u,wt));
      }
      PriorityQueue<pair> pq=new PriorityQueue<>((a,b)->a.wt-b.wt);
      pq.offer(new pair(src,0));
      int dis[]=new int[V];
      for(int i=0;i<dis.length;i++){
          dis[i]=(int)1e9;
      }
      dis[src]=0;
      while(!pq.isEmpty()){
          pair p=pq.poll();
          int node=p.node;
          int wt=p.wt;
          if(wt>dis[node]){
              continue;
          }
          for(pair it:li.get(node)){
              int gnode=it.node;
              int gwt=it.wt;
              if(dis[node]+gwt<dis[gnode]){
                  dis[gnode]=dis[node]+gwt;
                  pq.offer(new pair(gnode,dis[gnode]));
              }
          }
      }
      ArrayList<Integer> ans=new ArrayList<>();
      for(int i=0;i<dis.length;i++){
          ans.add(dis[i]);
      }
      return ans;
    }
}
```
