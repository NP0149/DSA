```
class Solution {
    static void dfs(char arr[][],int row,int col,int visited[][]){
        visited[row][col]=1;
        for(int i=-1;i<=1;i++){
            for(int j=-1;j<=1;j++){
                int newr=row+i;
                int newc=col+j;
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]=='L' && visited[newr][newc]!=1){
                    dfs(arr,newr,newc,visited);
                }
            }
        }
    }
    public int countIslands(char[][] grid) {
        // Code here
        int visited[][]=new int[grid.length][grid[0].length];
        int count=0;
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[0].length;j++){
                if(grid[i][j]=='L' && visited[i][j]!=1){
                    ++count;
                    dfs(grid,i,j,visited);
                }
            }
        }
        return count;
    }
}
```
