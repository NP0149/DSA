# Iterative PostOrder

[Problem Link](https://leetcode.com/problems/binary-tree-postorder-traversal/)

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
    static List<Integer> postorder(TreeNode root){
        Stack<TreeNode> st=new Stack<>();
        List<Integer> li=new ArrayList<>();
         if(root==null){
            return li;
        }
        st.push(root);
        while(!st.isEmpty()){
            TreeNode node=st.pop();
        li.add(node.val);
          if(node.left!=null){
       st.push(node.left);
        }
        if(node.right!=null){
        st.push(node.right);
        }
        }
        Collections.reverse(li);
       return li;
    }
    public List<Integer> postorderTraversal(TreeNode root) {
      return postorder(root);
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
