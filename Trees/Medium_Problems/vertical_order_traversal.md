[Problem Link](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)


```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    TreeMap<Integer,TreeMap<Integer,ArrayList<Integer>> tm=new TreeMap<>();
    void dfs(TreeNode root,int row,int col){
        if(root==null){
            return;
        }
        tm.putIfAbsent(col,new TreeMap<>());
        tm.get(col).putIfAbsent(row,new ArrayList<>());
        tm.get(col).get(row).add(root.val);

        dfs(root.left,row+1,col-1);
        dfs(root.right,row+1,col+1);
    }
    public List<List<Integer>> verticalTraversal(TreeNode root) {
       dfs(root,0,0);
       List<List<Integer>> ans=new ArrayList<>();
      for(TreeMap<Integer,ArrayList<Integer>> rows:tm.values()){
        List<Integer> temp=new ArrayList<>();
        for(ArrayList<Integer> li:rows.values()){
            Collections.sort(li);
            temp.addAll(li);
        }
        ans.add(temp);
      }
      return ans;
    }
}
```
