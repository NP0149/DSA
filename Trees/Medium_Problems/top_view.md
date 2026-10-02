[Problem Link](https://takeuforward.org/practice/dsa/top-view-of-bt)


```

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int data;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int val) { data = val; left = null, right = null }
 * }
 **/

class Solution {
    class pair{
        TreeNode node;
         int col;
         pair(TreeNode node,int col){
            this.node=node;
            this.col=col;
         }
    }
    public List<Integer> topView(TreeNode root) {
        TreeMap<Integer,Integer> tm=new TreeMap<>();
        Queue<pair> q=new LinkedList<>();
        q.offer(new pair(root,0));
        while(!q.isEmpty()){
            pair p=q.poll();
            TreeNode node=p.node;
            int col=p.col;
            tm.putIfAbsent(col,node.data);
            if(node.left!=null){
                q.offer(new pair(node.left,col-1));
            }
            if(node.right!=null){
                q.offer(new pair(node.right,col+1));
            }
        }
        List<Integer> ans=new ArrayList<>();
        for(int num:tm.keySet()){
            ans.add(tm.get(num));
        }
        return ans;
    }   
}
```
