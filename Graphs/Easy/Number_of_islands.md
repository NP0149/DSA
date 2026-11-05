# number of islands


[Problem link](https://leetcode.com/problems/number-of-islands/)

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
# BFS

```
class Solution {
    public int numIslands(char[][] grid) {
        int m=grid.length;
        int n=grid[0].length;
        int visited[][]=new int[m][n];
        int rows[]={-1,0,1,0};
        int cols[]={0,1,0,-1};
        int count=0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]=='1' && visited[i][j]!=1){
                    count++;
                    Queue<int[]> q=new LinkedList<>();
                    q.offer(new int[]{i,j});
                    while(!q.isEmpty()){
                        int arr[]=q.poll();
                        int row=arr[0];
                        int col=arr[1];
                       for(int i1=0;i1<4;i1++){
                        int newr=row+rows[i1];
                        int newc=col+cols[i1];
                        if(newr>=0 && newr<m && newc>=0 && newc<n && grid[newr][newc]=='1' && visited[newr][newc]==0){
                            q.offer(new int[]{newr,newc});
                            visited[newr][newc]=1;
                        }
                       }
                    }
                }
            }
        }
        return count;
    }
}
```
