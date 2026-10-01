

# the usual dfs will give u TLE

```
class Solution {
    class pair{
        int row;
        int col;
        int steps;
        pair(int row,int col,int steps){
            this.row=row;
            this.col=col;
            this.steps=steps;
        }
    }
    public int shortestPath(int[][] arr, int[] src, int[] dest) {
       if(arr[src[0]][src[1]]==0){
           return -1;
       }
       if(arr[dest[0]][dest[1]]==0){
           return -1;
       }
       int visited[][]=new int[arr.length][arr[0].length];
       int rows[]={-1,0,1,0};
       int cols[]={0,1,0,-1};
       Queue<pair> q=new LinkedList<>();
       q.offer(new pair(src[0],src[1],0));
       while(!q.isEmpty()){
           pair p=q.poll();
           int row=p.row;
           int col=p.col;
           int steps=p.steps;
           if(row==dest[0] && col==dest[1]){
               return steps;
           }
           for(int i=0;i<4;i++){
               int newr=row+rows[i];
               int newc=col+cols[i];
               if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==1 && visited[newr][newc]!=1){
                   visited[newr][newc]=1;
                   q.offer(new pair(newr,newc,steps+1));
               }
           }
       }
       
       return -1;
    }
}
```



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
