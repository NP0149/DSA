[Problem Link](https://www.geeksforgeeks.org/problems/maximum-connected-group/1)

# Brute it will give u TLE wont even run a single test case in GFG
```
class Solution {
    static int max_len;
    int rows[]={-1,0,1,0};
    int cols[]={0,1,0,-1};
    void dfs(int arr[][],int row,int col,int visited[][],int count){
        visited[row][col]=1;
        max_len=Math.max(max_len,count);
        for(int i=0;i<4;i++){
            int newr=row+rows[i];
            int newc=col+cols[i];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==1 && visited[newr][newc]!=1){
                dfs(arr,newr,newc,visited,count+1);
            }
        }
        visited[row][col]=0;
        
    }
    public int maxConnection(int arr[][]) {
        max_len=Integer.MIN_VALUE;
        int visited[][]=new int[arr.length][arr[0].length];
     for(int i=0;i<arr.length;i++){
         for(int j=0;j<arr[0].length;j++){
             if(arr[i][j]==0){
                 arr[i][j]=1;
                 dfs(arr,i,j,visited,1);
                 arr[i][j]=0;
             }
         }
     }
     return max_len;
        
    }
}
```

# Optimised

```

```
