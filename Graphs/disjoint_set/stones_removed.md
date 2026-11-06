# number of stones those are need to be removed


```
class Solution {
    int parent[];
    int size[];
    boolean used[];
    int find(int node){
        if(parent[node]==node){
            return node;
        }
        return parent[node]=find(parent[node]);
    }
    void union(int x,int y){
        int p1=find(x);
        int p2=find(y);
       if(p1==p2){
           return;
       }
       if(size[p1]>size[p2]){
          size[p1]+=size[p2];
          parent[p2]=p1;
       }
       else if(size[p1]<size[p2]){
          size[p2]+=size[p1];
          parent[p1]=p2;
       }
       else{
          size[p1]+=size[p2];
          parent[p2]=p1;
       }
    }
    public int removeStones(int[][] arr) {
      int max_row=0;
      int max_col=0;
      for(int a[]:arr){
        max_row=Math.max(max_row,a[0]);
        max_col=Math.max(max_col,a[1]);
      }
      int n=max_row+max_col+1;

      parent=new int[n+1];
      size=new int[n+1];
      used=new boolean[n+1];
      for(int i=0;i<=n;i++){
        parent[i]=i;
        size[i]=1;
        used[i]=false;
      }

      for(int a[]:arr){
        int row=a[0];
        int col=a[1];
        int col_node=col+max_row+1;
        used[row]=true;
        used[col_node]=true;
           if(find(row)!=find(col_node)){
            union(row,col_node);
           }
        
      }
    int sum=0;
    for(int i=0;i<size.length;i++){
        if(used[i] && parent[i]==i){
            sum+=1;
        }
    }
    return arr.length-sum;

    }
}
```

```

class dsu{
    private int[]rank;
    public int []parent;
    dsu(int v){
        rank=new int[v];
        parent=new int[v];
        for(int i=0;i<v;i++){
            rank[i]=0;
            parent[i]=i;
        }
    }
    public int find(int node){
        if(parent[node]!=node){
            return parent[node]=find(parent[node]);
        }
        return parent[node];
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
                parent[p2]=p1;
                rank[p1]++;
            }
        }
    }
}

class Solution {
    public int removeStones(int[][] arr) {
        int max_row=0;
        int max_col=0;
        for(int i=0;i<arr.length;i++){
            max_row=Math.max(max_row,arr[i][0]);
            max_col=Math.max(max_col,arr[i][1]);
        }
        dsu d=new dsu(max_row+max_col+2);
       for(int a[]:arr){
        int row=a[0];
        int col=max_row+a[1]+1;
        if(d.find(row)!=d.find(col)){
            d.union(row,col);
        }
       }
       int count=0;
       int v=max_row+max_col+2;
       HashMap<Integer,Integer> hm=new HashMap<>();
       for(int i=0;i<v;i++){
        hm.put(d.find(i),hm.getOrDefault(d.find(i),0)+1);
       }
       for(int num:hm.keySet()){
        if(hm.get(num)>1){
            count++;
        }
       }
       return arr.length-count;
    }
}
```
