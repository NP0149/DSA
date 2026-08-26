# Brute

```
class Solution {
    static int min_abs;
    static int max_diff;
   static int rows[]={-1,0,1,0};
    static int cols[]={0,-1,0,1};
    static void find(int arr[][],int row,int col,int max_diff,int visited[][]){
        visited[row][col]=1;
        if(row==arr.length-1 && col==arr[0].length-1){
          min_abs=Math.min(min_abs,max_diff);
          visited[row][col]=0;
          return;
        }
        for(int i=0;i<4;i++){
            int newr=row+rows[i];
            int newc=col+cols[i];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && visited[newr][newc]!=1){
                int new_diff=Math.max(max_diff,(int)Math.abs(arr[newr][newc]-arr[row][col]));
                find(arr,newr,newc,new_diff,visited);
            }
        }
       visited[row][col]=0;
       return;
    }
    public int minimumEffortPath(int[][] arr) {
        min_abs=Integer.MAX_VALUE;
        max_diff=Integer.MIN_VALUE;
        int visited[][]=new int[arr.length][arr[0].length];
        if(arr.length==1 && arr[0].length==1){
            return 0;
        }
        find(arr,0,0,max_diff,visited);
        return min_abs;
    }
}
```

# Optimal 


```

class pair{
    int diff;
    int row;
    int col;
    pair(int row,int col,int diff){
        this.diff=diff;
        this.row=row;
        this.col=col;
    }
}
class Solution {
    public int minimumEffortPath(int[][] arr) {
        int visited[][]=new int[arr.length][arr[0].length];
        for(int i=0;i<arr.length;i++){
            Arrays.fill(visited[i],-1);
        }
        PriorityQueue<pair> pq=new PriorityQueue<>((a,b)->a.diff-b.diff);
        pq.offer(new pair(0,0,0));
        int dis[][]=new int[arr.length][arr[0].length];
        for(int i=0;i<arr.length;i++){
            Arrays.fill(dis[i],Integer.MAX_VALUE);
        }
        dis[0][0]=0;
        int rows[]={-1,0,1,0};
        int cols[]={0,1,0,-1};
        while(!pq.isEmpty()){
            pair p=pq.poll();
            int row=p.row;
            int col=p.col;
            int diff=p.diff;
            for(int i=0;i<4;i++){
                int newr=row+rows[i];
                int newc=col+cols[i];
                if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length){
                     int d=Math.max(diff,(int)Math.abs(arr[newr][newc]-arr[row][col]));
                     if(d<dis[newr][newc]){
                    dis[newr][newc]=d;
                    pq.offer(new pair(newr,newc,d));
                     }
                }
            }
        }
        if(dis[arr.length-1][arr[0].length-1]==Integer.MAX_VALUE){
            return -1;
        }
        return dis[arr.length-1][arr[0].length-1];
    }
}
```
