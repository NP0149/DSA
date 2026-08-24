# Bipartite


## Using DFS
```
class Solution {

    static boolean is_bipartite(int arr[][],int visited[],int indx,int color){
        visited[indx]=color;
        for(int num:arr[indx]){
            if(visited[num]!=0){
                if(visited[num]==color){
                    return false;
                }
            }
            else{
                if(is_bipartite(arr,visited,num,3-color)==false){
                    return false;
                }
            }
        }
        return true;
    }
    public boolean isBipartite(int[][] arr) {
        int visited[]=new int[arr.length];
        for(int i=0;i<visited.length;i++){
            if(visited[i]==0){
               if(is_bipartite(arr,visited,i,1)==false){
                return false;
               }
            }
        }
    return true;
    }
}
```

## Using BFS

```
class Solution {
    public boolean isBipartite(int[][] arr) {
        int color[]=new int[arr.length];
        for(int i=0;i<color.length;i++){
            if(color[i]==0){
                Queue<Integer> q=new LinkedList<>();
                q.offer(i);
                color[i]=1;
                while(!q.isEmpty()){
                    int node=q.poll();
                    for(int num:arr[node]){
                        if(color[num]==0){
                            color[num]=3-color[node];
                            q.offer(num);
                        }
                        else{
                            if(color[num]==color[node]){
                                return false;
                            }
                        }
                    }
                }
            }
        }
        return true;
    }
}
```
