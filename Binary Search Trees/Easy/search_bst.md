# search in binary search tree

[Problem Link](https://takeuforward.org/practice/dsa/search-in-bst)

in BST we have left value less than the root value and right value greater than the root.val


```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int data;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int val) { data = val; left = null, right = null }
 * }
 **/

class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
        if(root==null){
            return null;
        }
        if(root.data==val){
            return root;
        }
       if(val<root.data){
        return searchBST(root.left,val);
       }
       return searchBST(root.right,val);
    }
}
```
