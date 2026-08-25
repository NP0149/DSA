# Shotest path in undirected graph

```
class Solution {
    public int shortestPath(int V, int[][] arr, int src, int dest) {
        // code here
     List<List<Integer>> li=new ArrayList<>();
     for(int i=0;i<V;i++){
         li.add(new ArrayList<>());
     }
     for(int i=0;i<arr.length;i++){
         int u=arr[i][0];
         int v=arr[i][1];
         li.get(u).add(v);
         li.get(v).add(u);
     }
     int dis[]=new int[V];
     for(int i=0;i<V;i++){
         dis[i]=(int)1e9;
     }
     Queue<Integer> q=new LinkedList<>();
     q.offer(src);
     dis[src]=0;
     while(!q.isEmpty()){
         int top=q.poll();
         for(int num:li.get(top)){
             if(dis[top]+1<dis[num]){
                 dis[num]=dis[top]+1;
                 q.offer(num);
             }
         }
     }
 // Only check destination
 if(dis[dest] == (int)1e9) {
     return -1;
 }

 return dis[dest];
    }
}
```
