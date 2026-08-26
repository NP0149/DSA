# Brute

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
# Optimal

```
class pair{
    int row;
    int col;
    int wt;
    pair(int row,int col,int wt){
        this.row=row;
        this.col=col;
        this.wt=wt;
    }
}


class Solution {
    public int shortestPath(int[][] arr, int[] src, int[] dest) {
        if(arr[src[0]][src[1]]==0 || arr[dest[0]][dest[1]]==0){
            return -1;
        }
        if(src[0]==dest[0] && src[1]==dest[1]){
            return 0;
        }
      Queue<pair> q=new LinkedList<>();
      q.add(new pair(src[0],src[1],0));
      int rows[]={-1,0,1,0};
      int cols[]={0,-1,0,1};
      
      int dis[][]=new int[arr.length][arr[0].length];
      for(int i=0;i<arr.length;i++){
          Arrays.fill(dis[i],Integer.MAX_VALUE);
      }
      dis[src[0]][src[1]]=0;
      
      while(!q.isEmpty())
      {
          pair p=q.poll();
          int row=p.row;
          int col=p.col;
          int count=p.wt;
          for(int i=0;i<4;i++){
              int newr=row+rows[i];
              int newc=col+cols[i];
              if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]==1 && dis[newr][newc]>(1+dis[row][col])){
                  dis[newr][newc]=dis[row][col]+1;
                  if(newr==dest[0] && newc==dest[1]){
                      return count+1;
                  }
                  q.offer(new pair(newr,newc,dis[row][col]+1));
              }
          }
      }
      return -1;
        
    }
}
```
