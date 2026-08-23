# Sorrounded region

```
class Solution {
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
    static void dfs(int [][]visited,char arr[][],int i,int j){
     visited[i][j]=1;
     for(int k=0;k<4;k++){
        int newr=i+rows[k];
        int newc=j+cols[k];
        if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]=='O' && visited[newr][newc]!=1){
            dfs(visited,arr,newr,newc);
        }
     }
    }
    public void solve(char[][] arr) {
        int visited[][]=new int[arr.length][arr[0].length];
        for(int j=0;j<arr[0].length;j++){
            if(visited[0][j]!=1 && arr[0][j]=='O'){
                dfs(visited,arr,0,j);
            }
            if(visited[arr.length-1][j]!=1 && arr[arr.length-1][j]=='O'){
                dfs(visited,arr,arr.length-1,j);
            }
        }
        for(int j=0;j<arr.length;j++){
           if(visited[j][0]!=1 && arr[j][0]=='O'){
            dfs(visited,arr,j,0);
           }
           if(visited[j][arr[0].length-1]!=1 && arr[j][arr[0].length-1]=='O'){
            dfs(visited,arr,j,arr[0].length-1);
           }
        } 
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(visited[i][j]!=1 && arr[i][j]=='O'){
                    arr[i][j]='X';
                }
            }
        }
    }
}
```
