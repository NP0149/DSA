# Max diameter

[Problem Link](https://leetcode.com/problems/diameter-of-binary-tree/)

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
    static int height(TreeNode root,int []diameter){
        if(root==null){
            return 0;
        }
        int lh=height(root.left,diameter);
        int rh=height(root.right,diameter);
        diameter[0]=Math.max(diameter[0],lh+rh);
        return 1+Math.max(lh,rh);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        int diameter[]=new int[1];
        height(root,diameter);
        return diameter[0];
    }
}
```
```
class Solution {
    static int find_height(TreeNode root){
        if(root==null){
            return 0;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        return 1+Math.max(lh,rh);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        if(root==null){
            return 0;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        max_length=Math.max(max_length,lh+rh);

        int left=diameterOfBinaryTree(root.left);
        int right=diameterOfBinaryTree(root.right);

        return max_length;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
