# number of islands

```
class Solution {
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
    static void dfs(char arr[][],int visited[][],int i,int j){
        visited[i][j]=1;
       for(int k=0;k<4;k++){
        int newr=i+rows[k];
        int newc=j+cols[k];
        if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && visited[newr][newc]!=1 && arr[i][j]=='1'){
            dfs(arr,visited,newr,newc);
        }
       }
    }
    public int numIslands(char[][] arr) {
        int visited[][]=new int[arr.length][arr[0].length];
        int count=0;
       for(int i=0;i<arr.length;i++){
        for(int j=0;j<arr[0].length;j++){
            if(visited[i][j]==0 && arr[i][j]=='1'){
              count++;
              dfs(arr,visited,i,j);
            }
        }
       }
       return count;
    }
}
```
