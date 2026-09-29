# using priority Queue
[Problem Link](https://www.geeksforgeeks.org/problems/implementing-dijkstra-set-1-adjacency-matrix/1)

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
```
import java.util.*;

public class prac{

    static int find(int start,int end,int vertices,List<List<int[]>> li){
        PriorityQueue<int[]> pq=new PriorityQueue<>((a,b)->(a[0]-b[0]));
        int dis[]=new int[vertices];
        Arrays.fill(dis,Integer.MAX_VALUE);
        pq.offer(new int[]{start,0});
        dis[start]=0;
        while(!pq.isEmpty()){
            int []top=pq.poll();
            int node=top[0];
            int distance=top[1];
            for(int arr[]:li.get(node)){
                int destnode=arr[0];
                if(distance+arr[1]<dis[destnode]){
                    dis[destnode]=distance+arr[1];
                    pq.add(new int[]{destnode,dis[destnode]});
                }
            }
        }
        return dis[end];
    }
    public static void main(String args[]){
        int arr[][]={{0,1,2},{1,3,1},{0,2,5},{2,3,2}};
        List<List<int[]>> li=new ArrayList<>();
        int v=4;
        for(int i=0;i<v;i++){
            li.add(new ArrayList<>());
        }
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v1=arr[i][1];
            int val=arr[i][2];
            li.get(u).add(new int[]{v1,val});
        }
        System.out.println(find(0,v-1,v,li));
    }
}

```

