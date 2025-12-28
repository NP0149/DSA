# Lowest common factor

[Problem Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    static boolean find(TreeNode root,TreeNode p,List<TreeNode> li){
        if(root==null){
         return false;
        }
        li.add(root);
        if(root==p){
            return true;
        }
        if(find(root.right,p,li) || find(root.left,p,li)){
            return true;
        }
        li.remove(li.size()-1);
        return false;
    }
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        List<TreeNode> li=new ArrayList<>();
        find(root,p,li);
        List<TreeNode> al=new ArrayList<>();
        find(root,q,al);
        TreeNode lca=null;
       int len=Math.min(li.size(),al.size());
       for(int i=0;i<len;i++){
        if(li.get(i).val==al.get(i).val){
            lca=li.get(i);
        }
       }
      return lca;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(h)
