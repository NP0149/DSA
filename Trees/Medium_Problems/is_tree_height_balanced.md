
```
class Solution {
    int max_length=Integer.MIN_VALUE;
    int find(TreeNode root){
        if(root==null){
            return 0;
        }
        int left=find(root.left);
        int right=find(root.right);

        max_length=Math.max(max_length,left+right);

        return 1+Math.max(left,right);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        find(root);
        return max_length;
    }
}
```


```
class Solution {
    int find(TreeNode root){
      if(root==null){
        return 0;
      }
      int left=find(root.left);
      int right=find(root.right);
      return 1+Math.max(left,right);
    }
    public boolean isBalanced(TreeNode root) {
        //your code goes here
        if(root==null){
            return true;
        }
        int left=find(root.left);
        int right=find(root.right);
        if(Math.abs(left-right)>1){
            return false;
        }
        return isBalanced(root.left) && isBalanced(root.right);
	}
}
```

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
    static int find_height(TreeNode root){
        if(root==null){
            return 0;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        return 1+Math.max(lh,rh);
    }
    public boolean isBalanced(TreeNode root) {
        if(root==null){
            return true;
        }
        int lh=find_height(root.left);
        int rh=find_height(root.right);
        if(Math.abs(lh-rh)>1) return false;

        boolean lc=isBalanced(root.left);
        boolean rc=isBalanced(root.right);
         if(lc==false|| rc==false) return false;

         return true;
    }
}
```
