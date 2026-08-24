# topo sort bfs

```
class Solution {
    public ArrayList<Integer> topoSort(int v, int[][] arr) {
      int inorder[]=new int[v];
        List<List<Integer>> li=new ArrayList<>();
    for(int i=0;i<v;i++){
        li.add(new ArrayList<>());
    }
    
      for(int i=0;i<arr.length;i++){
          int u=arr[i][0];
          int v1=arr[i][1];
          li.get(u).add(v1);
          inorder[v1]++;
      }
      Queue<Integer> q=new LinkedList<>();
    for(int i=0;i<inorder.length;i++){
        if(inorder[i]==0){
            q.offer(i);
        }
    }
    ArrayList<Integer> ans=new ArrayList<>();
      while(!q.isEmpty()){
          int top=q.poll();
          ans.add(top);
          for(int num:li.get(top)){
              inorder[num]--;
              if(inorder[num]==0){
                  q.offer(num);
              }
          }
      }
      return ans;
        
    }
}
```
