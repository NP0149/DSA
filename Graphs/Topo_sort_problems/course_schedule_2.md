```
class Solution {
    public int[] findOrder(int v, int[][] arr) {
        int indegree[]=new int[v];
        List<List<Integer>> li=new ArrayList<>();
        for(int i=0;i<v;i++){
            li.add(new ArrayList<>());
        }
        for(int i=0;i<arr.length;i++){
            int u=arr[i][0];
            int v1=arr[i][1];
           li.get(u).add(v1);
          indegree[v1]++;
        }
        Queue<Integer> q=new LinkedList<>();
        for(int i=0;i<indegree.length;i++){
            if(indegree[i]==0){
                q.offer(i);
            }
        }
        List<Integer> ans=new ArrayList<>();
      while(!q.isEmpty()){
        int top=q.poll();
        ans.add(top);
        for(int num:li.get(top)){
            indegree[num]--;
            if(indegree[num]==0){
                q.offer(num);
            }
        }
      }
      if(ans.isEmpty() || ans.size()<v){
        return new int[0];
      }
      int topo[]=new int[v];

     for(int i=0;i<v;i++){
     topo[i]=ans.get(ans.size()-1-i);
     }
     return topo;
    }
}
```
