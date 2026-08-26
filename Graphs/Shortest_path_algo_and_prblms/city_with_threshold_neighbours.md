# City with threshold neighbours

```
class Solution {
    public int findTheCity(int n, int[][] arr, int threshold) {
        int dis[][]=new int[n][n];
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==j){
                    dis[i][j]=0;
                }
             else{
                dis[i][j]=(int)1e8;
             }
            }
        }
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v=arr[i][1];
            int wt=arr[i][2];
            dis[u][v]=wt;
            dis[v][u]=wt;
        }
      for(int k=0;k<n;k++){
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(dis[i][k]!=(int)1e8 && dis[k][j]!=(int)1e8){
                dis[i][j]=Math.min(dis[i][j],dis[i][k]+dis[k][j]);
                }
            }
        }
      }
      int count_node[]=new int[n];
      for(int i=0;i<n;i++){
         int count=0;
         for(int j=0;j<n;j++){
            if(dis[i][j]<=threshold){
                count++;
            }
         }
         count_node[i]=count;
      }
      int min=Integer.MAX_VALUE;
      for(int i=0;i<n;i++){
        min=Math.min(min,count_node[i]);
      }
      int city=-1;
      for(int i=0;i<n;i++){
        if(count_node[i]==min)
        {
         city=i;
        }
      }
      return city;
    }
}
```
