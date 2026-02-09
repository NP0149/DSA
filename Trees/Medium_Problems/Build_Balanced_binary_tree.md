# Build balanced binary tree

[Problem Link](https://leetcode.com/problems/balance-a-binary-search-tree/description/?envType=daily-question&envId=2026-02-09)

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
    static void inorder(List<Integer> li,TreeNode root){
        if(root==null) return;
        inorder(li,root.left);
        li.add(root.val);
        inorder(li,root.right);
    }
    static TreeNode build_balanced(List<Integer> li,int start,int end){
        if(start>end) return null;
        int mid=(start+end)/2;
        TreeNode root=new TreeNode(li.get(mid));
        root.left=build_balanced(li,start,mid-1);
        root.right=build_balanced(li,mid+1,end);
        return root;

    }
    public TreeNode balanceBST(TreeNode root) {
        List<Integer> li=new ArrayList<>();
        inorder(li,root);
        return build_balanced(li,0,li.size()-1);
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
