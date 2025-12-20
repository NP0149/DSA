# Iterative Inorder

[Problem Link](https://leetcode.com/problems/binary-tree-inorder-traversal/)

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
    public List<Integer> inorderTraversal(TreeNode root) {
        Stack<TreeNode> st=new Stack<>();
        List<Integer> li=new ArrayList<>();
        if(root==null){
            return li;
        }
        TreeNode curr=root;
       while(!st.isEmpty() || curr!=null){
        while(curr!=null){
            st.push(curr);
            curr=curr.left;
        }
       curr=st.pop();
       li.add(curr.val);
       curr=curr.right;
       }
        return li;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
