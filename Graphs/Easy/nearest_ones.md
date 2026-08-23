# nearest ones from zeroes

```
class Solution {
    static class pair{
        int i,j,d;
        pair(int i,int j,int d){
            this.i=i;
            this.j=j;
            this.d=d;
        }
    }
    public int[][] updateMatrix(int[][] arr) {

         Queue<pair> q=new LinkedList<>();

        int dis[][]=new int[arr.length][arr[0].length];

        int visited[][]=new int[arr.length][arr[0].length];

        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(arr[i][j]==0){
                    q.offer(new pair(i,j,0));
                    visited[i][j]=1;
                }
            }
        }
        while(!q.isEmpty()){
            pair p=q.poll();
            int i=p.i;
            int j=p.j;
            int d=p.d;
            dis[i][j]=d;
            int rows[]={-1,0,1,0};
            int cols[]={0,1,0,-1};
            for(int k=0;k<4;k++){
                int newr=i+rows[k];
                int newc=j+cols[k];
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && visited[newr][newc]!=1){
                    q.offer(new pair(newr,newc,d+1));
                    visited[newr][newc]=1;
                }
            }
        }
        return dis;
        
    }
}
```
