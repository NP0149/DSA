# Bipartite


## Using DFS
```
class Solution {
    static boolean dfs(int arr[][],int color[],int indx,int coloring){
        color[indx]=coloring;
        for(int num:arr[indx]){
            if(color[num]==0){
                if(dfs(arr,color,num,3-coloring)==false){
                  return false;
                }
            }
            else{
                if(color[num]==color[indx]){
                    return false;
                }
            }
        }
        return true;
    }
    public boolean isBipartite(int[][] arr) {
        int color[]=new int[arr.length];
        for(int i=0;i<arr.length;i++){
            if(color[i]==0){
                if(!dfs(arr,color,i,1)){
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
