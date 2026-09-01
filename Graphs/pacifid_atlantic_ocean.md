[Problem Link](https://leetcode.com/problems/pacific-atlantic-water-flow/)


```
class Solution {
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
    void dfs(int arr[][],int row,int col,int visited[][]){
        visited[row][col]=1;
        for(int i=0;i<4;i++){
            int newr=row+rows[i];
            int newc=col+cols[i];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && visited[newr][newc]!=1 && arr[newr][newc]>=arr[row][col]){
                dfs(arr,newr,newc,visited);
            }
        }
    }
    public List<List<Integer>> pacificAtlantic(int[][] arr) {
     int pacific[][]=new int[arr.length][arr[0].length];
     int atlantic[][]=new int[arr.length][arr[0].length];
     //first row
     for(int i=0;i<arr[0].length;i++){
        dfs(arr,0,i,pacific);
     }
     //first col
     for(int j=0;j<arr.length;j++){
        dfs(arr,j,0,pacific);
     }
     //last row
     for(int i=0;i<arr[0].length;i++){
        dfs(arr,arr.length-1,i,atlantic);
     }
     //last col
     for(int j=0;j<arr.length;j++){
        dfs(arr,j,arr[0].length-1,atlantic);
     }
     List<List<Integer>> li=new ArrayList<>();
     for(int i=0;i<arr.length;i++){
        for(int j=0;j<arr[0].length;j++){
            if(pacific[i][j]==1 && atlantic[i][j]==1){
                List<Integer> temp=new ArrayList<>();
                temp.add(i);
                temp.add(j);
              li.add(temp);
            }
        }
     }
     return li;
    }

}
```
