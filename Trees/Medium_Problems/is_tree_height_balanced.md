
```
class Solution {
    boolean find(TreeNode p,TreeNode q){
         if(p==null && q==null){
            return true;
        }
        if(p==null || q==null || p.val!=q.val){
            return false;
        }
        boolean left=find(p.left,q.left);
        boolean right=find(p.right,q.right);
        if(left==false || right==false){
            return false;
        }
        return true;
    }
    public boolean isSameTree(TreeNode p, TreeNode q) {
    return find(p,q);
    }
}
```

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
    static int find_height(TreeNode root){
        if(root==null){
            return 0;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        return 1+Math.max(lh,rh);
    }
    public boolean isBalanced(TreeNode root) {
        if(root==null){
            return true;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        if(Math.abs(lh-rh)>1) return false;

        boolean lc=isBalanced(root.left);
        boolean rc=isBalanced(root.right);
         if(lc==false|| rc==false) return false;

         return true;
    }
}
```
