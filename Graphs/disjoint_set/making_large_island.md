[Problem Link](https://leetcode.com/problems/making-a-large-island/description/)

```
class Solution {
    static int maxarea;
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
   int dfs(int arr[][],int row,int col,int visited[][]){
    visited[row][col]=1;
    int count=1;
    for(int i=0;i<4;i++){
        int newr=row+rows[i];
        int newc=col+cols[i];
        if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==1 && visited[newr][newc]!=1){
            count+=dfs(arr,newr,newc,visited);
        }
    }
    return count;
   }
    public int largestIsland(int[][] arr) {
        maxarea=Integer.MIN_VALUE;
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(arr[i][j]==0){
                    arr[i][j]=1;
                    int visited[][]=new int[arr.length][arr[0].length];
                    int area=dfs(arr,i,j,visited);
                     maxarea=Math.max(maxarea,area);
                    arr[i][j]=0;
                }
            }
        }
        if(maxarea==Integer.MIN_VALUE){
            return arr.length*arr[0].length;
        }
        return maxarea;
    }
}
```
