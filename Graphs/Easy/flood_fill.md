```
   class Solution {
    static class pair{
        int i;
        int j;
        int color;
        pair(int i,int j,int color){
            this.i=i;
            this.j=j;
            this.color=color;
        }
    }
    public int[][] floodFill(int[][] arr, int sr, int sc, int coloring) {
       if(arr[sr][sc]==coloring){
        return arr;
       }
        int visited[][]=new int[arr.length][arr[0].length];
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                visited[i][j]=arr[i][j];
            }
        }
           int originalcolor=arr[sr][sc];
        visited[sr][sc]=coloring;
        Queue<pair> q=new LinkedList<>();
        q.offer(new pair(sr,sc,coloring));

        int rows[]={-1,0,1,0};
        int cols[]={0,1,0,-1};
        while(!q.isEmpty()){
            pair p=q.poll();
            int i=p.i;
            int j=p.j;
            int color=p.color;
            for(int k=0;k<4;k++){
                int newr=i+rows[k];
                int newc=j+cols[k];
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length  && arr[newr][newc]==originalcolor && visited[newr][newc]==originalcolor){
                    q.offer(new pair(newr,newc,color));
                    visited[newr][newc]=color;
                }
            }
        }
        return visited;

    }
}
```
