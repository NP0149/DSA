[Problem Link](https://takeuforward.org/practice/dsa/bottom-view-of-bt)


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
    public List<Integer> bottomView(TreeNode root) {
        //your code goes here
       Queue<pair> q=new LinkedList<>();
       TreeMap<Integer,Integer> tm=new TreeMap<>();
       q.offer(new pair(root,0));
       while(!q.isEmpty()){
        pair p=q.poll();
        TreeNode node=p.node;
        int col=p.col;
        tm.put(col,node.data);
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
