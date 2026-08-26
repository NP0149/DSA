```
class Solution {
    static int mincount;
    static int rows[]={-1,0,1,0};
    static int cols[]={0,-1,0,1};
    static void find(int arr[][],int src[],int dest[],int row,int col,int count,int visited[][]){
        visited[row][col]=1;
        if(row==dest[0] && col==dest[1]){
            mincount=Math.min(mincount,count);
            visited[row][col]=0;
            return;
        }
        for(int i=0;i<4;i++){
                int newr=row+rows[i];
                int newc=col+cols[i];
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==1 && visited[newr][newc]!=1){
                    find(arr,src,dest,newr,newc,count+1,visited);
                }
            }
        visited[row][col]=0;
        return;
    }
    public int shortestPath(int[][] arr, int[] src, int[] dest) {
        mincount=Integer.MAX_VALUE;
     if(arr[src[0]][src[1]]==0 || arr[dest[0]][dest[1]]==0){
         return -1;
     }
     int visited[][]=new int[arr.length][arr[0].length];
     find(arr,src,dest,src[0],src[1],0,visited);
     if(mincount==Integer.MAX_VALUE){
         return -1;
     }
     return mincount;
     
    }
    
}
```
