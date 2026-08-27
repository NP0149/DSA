# Kruskal

```

class dsu{
    private int rank[];
    private int parent[];
    dsu(int v){
        rank=new int[v];
        parent=new int[v];
        for(int i=0;i<v;i++){
            rank[i]=0;
            parent[i]=i;
        }
    }
    
    public int find(int i){
        if(parent[i]!=i){
            return parent[i]=find(parent[i]);
        }
        return parent[i];
    }
    
    public void union(int x,int y){
        int p1=find(x);
        int p2=find(y);
        
        if(p1!=p2){
            if(rank[p1]>rank[p2]){
                parent[p2]=p1;
            }
            else if(rank[p1]<rank[p2]){
                parent[p1]=p2;
            }
            else{
                parent[p1]=p2;
                rank[p2]++;
            }
        }
    }
}


class Solution {
    static int kruskalsMST(int v, int[][] arr) {
        dsu d=new dsu(v);
        int cost=0;
        int count=0;
        Arrays.sort(arr,(a,b)->Integer.compare(a[2],b[2]));
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v1=arr[i][1];
            int wt=arr[i][2];
            if(d.find(u)!=d.find(v1)){
                d.union(u,v1);
                cost+=wt;
                ++count;
                if(count==v-1){
                    break;
                }
            }
        }
        return cost;
    }
}

```
