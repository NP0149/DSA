# Inorder Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-inorder-traversal/submissions/1701532482/)

# Approach-I

1)Need to print left,root,right

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
    public static void inorder(TreeNode node,List<Integer> al){
        if(node==null){
            return;
        }
        else{
            inorder(node.left,al);
            al.add(node.val);
            inorder(node.right,al);
        }
    }
    public List<Integer> inorderTraversal(TreeNode root) {
        ArrayList<Integer> al=new ArrayList<>();
        inorder(root,al);
        return al;
    }
}
```

# Complexitiy Analysis

Time:O(n)

Space:O(n)
