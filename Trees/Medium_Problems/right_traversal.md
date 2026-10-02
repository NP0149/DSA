[Problem Link](https://leetcode.com/problems/binary-tree-right-side-view/submissions/2160334583/)


```
class Solution {
    class pair{
        TreeNode node;
        int row;
        pair(TreeNode node,int row){
            this.node=node;
            this.row=row;
        }
    }
    public List<Integer> rightSideView(TreeNode root) {
           List<Integer> li=new ArrayList<>();
           if(root==null){
            return li;
           }
        Queue<pair> q=new LinkedList<>();
        TreeMap<Integer,Integer> tm=new TreeMap<>();
        q.offer(new pair(root,1));
        while(!q.isEmpty()){
            pair p=q.poll();
            TreeNode node=p.node;
            int row=p.row;
            tm.putIfAbsent(row,node.val);
            if(node.right!=null){
               q.offer(new pair(node.right,row+1));
            }
            if(node.left!=null){
              q.offer(new pair(node.left,row+1));
            }
        }
      for(int num:tm.keySet()){
        li.add(tm.get(num));
      }
   return li;
    }
}
```
