# Bellman ford algorithm

```
class Solution {
    public ArrayList<Integer> bellmanFord(int V, int[][] arr, int src) {
        ArrayList<Integer> li=new ArrayList<>();
        for(int i=0;i<V;i++){
            li.add((int)1e8);
        }
        li.set(src,0);
        for(int i=0;i<V-1;i++){
            for(int a[]:arr){
                int u=a[0];
                int v=a[1];
                int wt=a[2];
                if(li.get(u)!=(int)1e8 && li.get(u)+wt<li.get(v)){
                   li.set(v,li.get(u)+wt);
                }
            }
        }
        for(int a[]:arr){
            int u=a[0];
            int v=a[1];
            int wt=a[2];
            if(li.get(u)!=(int)1e8 && li.get(u)+wt<li.get(v)){
                ArrayList<Integer> al=new ArrayList<>();
                al.add(-1);
                return al;
            }
        }
        return li;
    }
}

```
