# Balanced Binary tree

[problem Link](https://leetcode.com/problems/balanced-binary-tree/submissions/1860921245/)

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
    static int find_maxi(TreeNode root){
        if(root==null){
            return 0;
        }
        int lh=find_maxi(root.left);
        int rh=find_maxi(root.right);
        if(rh==-1 || lh==-1){
            return -1;
        }
        if(Math.abs(lh-rh)>1){
            return -1;
        }
        return 1+Math.max(rh,lh);
    }
    public boolean isBalanced(TreeNode root) {
       if(find_maxi(root)==-1){
        return false;
       }
       return true;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(h)
