# Rotten oranges

```
class Solution {
    static class pair{
        int i;
        int j;
        int t;
        pair(int i,int j,int t){
            this.i=i;
            this.j=j;
            this.t=t;
        }
    }
    public int orangesRotting(int[][] arr) {
        int visited[][]=new int[arr.length][arr[0].length];
        Queue<pair> q=new LinkedList<>();
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(arr[i][j]==2){
                    visited[i][j]=2;
                    q.add(new pair(i,j,0));
                }
            }
        }

        int rows[]={1,0,-1,0};
        int cols[]={0,1,0,-1};
        int tm=0;
     while(!q.isEmpty()){
        pair p=q.poll();
        int r=p.i;
        int c=p.j;
        int t=p.t;
        tm=Math.max(tm,t);
       for(int i=0;i<rows.length;i++){
        int newr=r+rows[i];
        int newc=c+cols[i];
        if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length){
             if(arr[newr][newc]==1 && visited[newr][newc]!=2){
                q.offer(new pair(newr,newc,t+1));
                visited[newr][newc]=2;
             }
        }
       }
     }
     for(int i=0;i<arr.length;i++){
        for(int j=0;j<arr[0].length;j++){
            if(arr[i][j]==1 && visited[i][j]!=2){
                return -1;
            }
        }
     }
     return tm;
    }
}
```
