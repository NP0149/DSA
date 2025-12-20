# Level Order

[Problem Link](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> q=new LinkedList<>();
        List<List<Integer>> li=new ArrayList<>();
        q.offer(root);
        if(root==null){
            return li;
        }
        while(!q.isEmpty()){
            int len=q.size();
            List<Integer> small=new ArrayList<>();
            for(int i=0;i<len;i++){
                if(q.peek().left!=null){
                    q.offer(q.peek().left);
                }
                if(q.peek().right!=null){
                    q.offer(q.peek().right);
                }
                small.add(q.poll().val);
            }
            li.add(small);
        }
        return li;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
