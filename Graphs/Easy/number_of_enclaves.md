# number of enclaves

```
class Solution {
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
    static void dfs(int visited[][],int arr[][],int i,int j){
        visited[i][j]=1;
        for(int k=0;k<4;k++){
            int newr=i+rows[k];
            int newc=j+cols[k];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && visited[newr][newc]!=1 && arr[newr][newc]==1){
                dfs(visited,arr,newr,newc);
            }
        }
    }
    public int numEnclaves(int[][] arr) {
        int visited[][]=new int[arr.length][arr[0].length];
        //for rows
        for(int i=0;i<arr[0].length;i++){
           if(visited[0][i]!=1 && arr[0][i]==1){
            dfs(visited,arr,0,i);
           }
           if(visited[arr.length-1][i]!=1 && arr[arr.length-1][i]==1){
            dfs(visited,arr,arr.length-1,i);
           }
        }
        //cols
        for(int i=0;i<arr.length;i++){
            if(visited[i][0]!=1 && arr[i][0]==1){
                dfs(visited,arr,i,0);
            }
            if(visited[i][arr[0].length-1]!=1 && arr[i][arr[0].length-1]==1){
                dfs(visited,arr,i,arr[0].length-1);
            }
        }
        int count=0;
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(visited[i][j]!=1 && arr[i][j]==1){
                    count++;
                }
            }
        }
        return count;
    }
}
```
