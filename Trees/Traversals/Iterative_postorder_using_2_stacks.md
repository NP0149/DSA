# Iterative postorder using two stacks

[Problem Link](https://leetcode.com/problems/binary-tree-postorder-traversal/submissions/1860578277/)


Instead of list,take stack to store values and then add to answer list by poping the values stored list

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
      Stack<Integer> s=new Stack<>();
      List<Integer> li=new ArrayList<>();
         if(root==null){
            return li;
        }
        st.push(root);
        while(!st.isEmpty()){
            TreeNode node=st.pop();
       s.push(node.val);
          if(node.left!=null){
       st.push(node.left);
        }
        if(node.right!=null){
        st.push(node.right);
        }
        }
      while(!s.isEmpty()){
        li.add(s.pop());
      }
       return li;
    }
    public List<Integer> postorderTraversal(TreeNode root) {
      return postorder(root);
    }
}
```

# Complexity Analysis

Time:O(2n)

Space:O(3n)
