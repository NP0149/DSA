# Cycle undirected

```
class Solution {
    static class pair{
        int node;
        int parent;
        pair(int node,int parent){
            this.node=node;
            this.parent=parent;
        }
    }
    static boolean detect_cycle(List<List<Integer>> li,int indx,boolean visited[]){
        visited[indx]=true;
        Queue<pair> q=new LinkedList<>();
        q.offer(new pair(indx,-1));
        while(!q.isEmpty()){
            pair p=q.poll();
            int node=p.node;
            int parent=p.parent;
            List<Integer> child=li.get(node);
            for(int num:child){
                if(!visited[num]){
                    q.offer(new pair(num,node));
                    visited[num]=true;
                }
                else if(visited[num] && num!=parent){
                    return true;
                }
            }
        }
        return false;
    }
    public boolean isCycle(int v, int[][] edges) {
      List<List<Integer>> li=new ArrayList<>();
      for(int i=0;i<v;i++){
          li.add(new ArrayList<>());
      }
      for(int i=0;i<edges.length;i++){
          int u=edges[i][0];
          int v1=edges[i][1];
          li.get(u).add(v1);
          li.get(v1).add(u);
      }
      boolean visited[]=new boolean[v];
      for(int i=0;i<v;i++){
          if(!visited[i]){
              if(detect_cycle(li,i,visited)){
                  return true;
              }
          }
      }
      
      return false;
      
    }
}
```
