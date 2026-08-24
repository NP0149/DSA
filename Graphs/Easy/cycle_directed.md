# Cycle in a directed 


```
class Solution {
    static boolean dfs(List<List<Integer>> li,int visited[],int pathvisited[],int indx){
        visited[indx]=1;
        pathvisited[indx]=1;
        
        for(int num:li.get(indx)){
            if(visited[num]!=1){
                if(dfs(li,visited,pathvisited,num)==true){
                    return true;
                }
            }
            else{
                if(visited[num]==1 && pathvisited[num]==1){
                    return true;
                }
            }
        }
        
        pathvisited[indx]=0;
        return false;
    }
    public boolean isCyclic(int v, int[][] arr) {
      List<List<Integer>> li=new ArrayList<>();
      for(int i=0;i<v;i++){
          li.add(new ArrayList<>());
      }
      for(int i=0;i<arr.length;i++){
          int u=arr[i][0];
          int v1=arr[i][1];
         li.get(u).add(v1);
      }
      int visited[]=new int[v];
      int pathvisited[]=new int[v];
      for(int i=0;i<v;i++){
          if(dfs(li,visited,pathvisited,i)==true){
              return true;
          }
      }
        return false;
    }
}
```
