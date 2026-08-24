# Topo sort

```
class Solution {
    static void dfs(List<List<Integer>> li,int visited[],int indx,Stack<Integer> st){
        visited[indx]=1;
        for(int num:li.get(indx)){
            if(visited[num]!=1){
                dfs(li,visited,num,st);
            }
        }
        st.push(indx);
    }
    public ArrayList<Integer> topoSort(int v, int[][] arr) {
        List<List<Integer>> li=new ArrayList<>();
        for(int i=0;i<v;i++){
            li.add(new ArrayList<>());
        }
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v1=arr[i][1];
            li.get(u).add(v1);
        }
        int visited[]=new int[v];
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<v;i++){
            if(visited[i]!=1){
                dfs(li,visited,i,st);
            }
        }
        ArrayList<Integer> ans=new ArrayList<>();
        
    while(!st.isEmpty()){
            ans.add(st.pop());
        }
        return ans;
    }
}
```
