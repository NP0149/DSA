# PostOrder Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-postorder-traversal/)

# Approach-I

first print left,right and then root

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
    public static void postorder(TreeNode node,List<Integer> al){
        if(node==null){
            return;
        }
        else{
            postorder(node.left,al);
            postorder(node.right,al);
            al.add(node.val);
        }
    }
    public List<Integer> postorderTraversal(TreeNode root) {
        ArrayList<Integer> al=new ArrayList<>();
        postorder(root,al);
        return al;
    }
}
```
# Complexities

Time:O(n)

Space:O(n)
