# Iterative PreOrder Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-preorder-traversal/)

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
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> li=new ArrayList<>();
        Stack<TreeNode> st=new Stack<>();
         if(root==null){
            return li;
        }
        st.push(root);
        while(!st.isEmpty()){
         TreeNode node=st.pop();
         li.add(node.val);
          if(node.right!=null){
            st.push(node.right);
         }
         if(node.left!=null){
            st.push(node.left);
         }
        }
        return li;
    }
}
```

# Complexity Analysis

time:O(n)

Space:O(n)
