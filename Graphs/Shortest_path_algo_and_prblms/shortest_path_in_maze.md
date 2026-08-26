```
class Solution {
    static int mincount;
    static void find(int arr[][],int count,int row,int col,int vis[][]){
        vis[row][col]=1;
        if(row==arr.length-1 && col==arr[0].length-1){
            mincount=Math.min(mincount,count);
            vis[row][col]=0;
            return ;
        }
        for(int i=-1;i<2;i++){
            for(int j=-1;j<2;j++){
                int newr=row+i;
                int newc=col+j;
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==0 && vis[newr][newc]!=1){
                     find(arr,count+1,newr,newc,vis);
                }
            }
        }
        vis[row][col]=0;
        return;
    }
    public int shortestPathBinaryMatrix(int[][] arr) {
        mincount=Integer.MAX_VALUE;
        int vis[][]=new int[arr.length][arr[0].length];
        if(arr[0][0]!=0 || arr[arr.length-1][arr.length-1]!=0){
            return -1;
        }
        find(arr,1,0,0,vis);
        if(mincount==Integer.MAX_VALUE){
            return -1;
        }
        return mincount;
    }
}
```
