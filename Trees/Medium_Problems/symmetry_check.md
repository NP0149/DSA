# Symmetry check 

[Problem link](https://leetcode.com/problems/symmetric-tree/)


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
    static boolean isSymmetry(TreeNode left,TreeNode right){
        if(left==null && right==null){
            return true;
        }
        if(left==null || right==null){
         return false;
        }
        if(left.val!=right.val){
            return false;
        }
            return isSymmetry(left.left,right.right) && isSymmetry(left.right,right.left);
    }
    public boolean isSymmetric(TreeNode root) {
        if(root==null){
            return true;
        }
        return isSymmetry(root.left,root.right);
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(h)


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
    boolean find(TreeNode rootp,TreeNode rootq){
        if(rootp==null && rootq!=null){
            return false;
        }
        if(rootq==null && rootp!=null){
            return false;
        }

        if(rootp!=null && rootq!=null){
            boolean left=find(rootp.right,rootq.left);
            if(rootp.val!=rootq.val){
                return false;
            }
            boolean right=find(rootp.left,rootq.right);

            if(left==false || right==false){
                return false;
            }
        }
        return true;
    }
    public boolean isSymmetric(TreeNode root) {
        if(root==null){
            return true;
        }
        return find(root.right,root.left);
    }
}
```
