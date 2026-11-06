

[Problem Link](https://leetcode.com/problems/making-a-large-island/)

## you need to make a large island by converting only one zero to one 

```
class Solution {
    int parent[];
    int size[];
     int find(int node){
        if(parent[node]==node){
            return node;
        }
        return parent[node]=find(parent[node]);
     }
   void  union(int x,int y){
    int p1=find(x);
    int p2=find(y);
    if(p1==p2){
        return;
    }
    if(size[p1]>size[p2]){
        parent[p2]=p1;
        size[p1]+=size[p2];
    }
    else if(size[p1]<size[p2]){
        parent[p1]=p2;
        size[p2]+=size[p1];
    }
    else{
        parent[p2]=p1;
        size[p1]+=size[p2];
    }
   }
    public int largestIsland(int[][] grid) {
        int n=grid.length;
        parent=new int[n*n];
        size=new int[n*n];
        for(int i=0;i<n*n;i++){
            parent[i]=i;
            size[i]=1;
        }
        int rows[]={-1,0,1,0};
        int cols[]={0,1,0,-1};
  int visited[][]=new int[n][n];
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
             if(grid[i][j]==1 && visited[i][j]!=1){
               int node=i*n+j;
              for(int k=0;k<4;k++){
                int newr=i+rows[k];
                int newc=j+cols[k];
                if(newr>=0 && newr<n && newc>=0 && newc<n && grid[newr][newc]==1){
                    int new_node=newr*n+newc;
                    if(find(node)!=find(new_node)){
                    union(node,new_node);
                    }
                }
              }
             }
            }
        }
       int max=0;
       for(int i=0;i<size.length;i++){
        if(parent[i]==i){
            max=Math.max(max,size[i]);
        }
       }
       for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(grid[i][j]==0){
                HashSet<Integer> hs=new HashSet<>();
                for(int k=0;k<4;k++){
                    int newr=i+rows[k];
                    int newc=j+cols[k];
                    if(newr>=0 && newr<n && newc>=0 && newc<n && grid[newr][newc]==1){
                        int node=newr*n+newc;
                        hs.add(find(node));
                    }
                }
                int total=1;
                for(int num:hs){
                    total+=size[num];
                }
                max=Math.max(max,total);
            }
        }
       }
       return max;
    }
}
```
