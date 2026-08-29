[Problem Link](https://leetcode.com/problems/binary-tree-maximum-path-sum/)


```
class Solution {
    int max_len=Integer.MIN_VALUE;
    int find(TreeNode root){
        if(root==null){
            return 0;
        }
        int left=find(root.left);
        int right=find(root.right);
        max_len=Math.max(max_len,root.val+Math.max(0,left)+Math.max(0,right));
        return root.val+Math.max(0,Math.max(left,right));
    }
    public int maxPathSum(TreeNode root) {
        find(root);
        return max_len;
    }
}
```
