# Preorder Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-preorder-traversal/submissions/1701531634/)

# Approach-I

1)Preorder traversal means we need to print root,node left and node right

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
    public static void preorder(TreeNode node,List<Integer> al){
     if(node==null){
        return;
     }
     else{
         al.add(node.val);
        preorder(node.left,al);
        preorder(node.right,al);
     }
    }
    public List<Integer> preorderTraversal(TreeNode root) {
        ArrayList<Integer> al=new ArrayList<>();
        preorder(root,al);
        return al;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
