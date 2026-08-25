[Problem Link](https://leetcode.com/problems/find-eventual-safe-states/)

```
class Solution {
    public List<Integer> eventualSafeNodes(int[][] arr) {
        List<List<Integer>> li=new ArrayList<>();
        int indegree[]=new int[arr.length];
     for(int i=0;i<arr.length;i++){
      li.add(new ArrayList<>());
     }
// reverse the nodes parent should become child and viceversa
        for(int i=0;i<arr.length;i++){
          for(int num:arr[i]){
            li.get(num).add(i);
            indegree[i]++;
          }
        }
        List<Integer> ans=new ArrayList<>();
        Queue<Integer> q=new LinkedList<>();
        for(int i=0;i<arr.length;i++){
            if(indegree[i]==0){
            q.offer(i);
            }
        }
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
        Collections.sort(ans);
        return ans;

    }
}
```
