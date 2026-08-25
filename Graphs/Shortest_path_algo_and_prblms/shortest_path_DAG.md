

### find toposort using stack there u can get the sequence and after that apply method
```

class pair{
   int node;
   int wt;
   pair(int node,int wt){
       this.node=node;
       this.wt=wt;
   }
}
class Solution {
    static void toposort(ArrayList<ArrayList<pair>> li,int vis[],int indx,Stack<Integer> st,int dis[]){
        vis[indx]=1;
        for(int i=0;i<li.get(indx).size();i++){
            int node=li.get(indx).get(i).node;
            if(vis[node]==0){
                toposort(li,vis,node,st,dis);
            }
        }
        st.push(indx);
    }
    public ArrayList<Integer> shortestPath(int V, int[][] arr) {
     ArrayList<ArrayList<pair>> li=new ArrayList<>();
     for(int i=0;i<V;i++){
         li.add(new ArrayList<pair>());
     }
     for(int i=0;i<arr.length;i++){
         int u=arr[i][0];
         int v=arr[i][1];
         int wt=arr[i][2];
         li.get(u).add(new pair(v,wt));
     }
     int vis[]=new int[V];
     int dis[]=new int[V];
     Arrays.fill(dis,(int)1e9);
     Stack<Integer> st=new Stack<>();
     for(int i=0;i<V;i++){
         if(vis[i]==0){
             toposort(li,vis,i,st,dis);
         }
     }
    dis[0]=0;
     while(!st.isEmpty()){
         int top=st.pop();
         for(int i=0;i<li.get(top).size();i++){
             int node=li.get(top).get(i).node;
             int wt=li.get(top).get(i).wt;
             if(dis[top]+wt<dis[node]){
                 dis[node]=dis[top]+wt;
             }
         }
     }
     for(int i=0;i<dis.length;i++){
         if(dis[i]==(int)1e9){
             dis[i]=-1;
         }
     }
   ArrayList<Integer> ans=new ArrayList<>();
   for(int i=0;i<dis.length;i++){
       ans.add(dis[i]);
   }
   return ans;
    }
}
```
