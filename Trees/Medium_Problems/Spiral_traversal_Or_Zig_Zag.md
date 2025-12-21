# Spiral Traversal or Zig Zag Traversal

[Problem Link](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/submissions/1861441668/)

# Approach-I

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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        Queue<TreeNode> q=new LinkedList<>();
        List<List<Integer>> li=new ArrayList<>();
        if(root==null){
            return li;
        }
        q.offer(root);
        int count=0;
        while(!q.isEmpty()){
            List<Integer> al=new ArrayList<>();
            int size=q.size();
            for(int i=0;i<size;i++){
                TreeNode node=q.peek();
                if(node.left!=null){
                    q.offer(node.left);
                }
                if(node.right!=null){
                    q.offer(node.right);
                }
                al.add(q.poll().val);
            }
            if(count%2==0){
                li.add(al);
            }
            else{
                Collections.reverse(al);
                li.add(al);
            }
            count++;
        }
        return li;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
