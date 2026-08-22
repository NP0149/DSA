# Representation of graph

```
import java.util.*;

public class adj_list {
 static void addEdge(ArrayList<ArrayList<Integer>> graph,int u,int v){
     graph.get(u).add(v);
     graph.get(v).add(u);
 }

    public static void main(String args[]) {
    int v=4;
    ArrayList<ArrayList<Integer>> graph=new ArrayList<>();
    for(int i=0;i<v;i++){
         graph.add(new ArrayList<>());
    }
    addEdge(graph,0,1);
    addEdge(graph,0,2);
    addEdge(graph,1,3);
    addEdge(graph,2,3);
    for(int i=0;i<v;i++){
        System.out.println(i+"->"+graph.get(i));
    }
    }
}
```
