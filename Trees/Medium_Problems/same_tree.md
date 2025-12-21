# Same tree

[Problem Link](https://leetcode.com/problems/same-tree/)

# Brute Force
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
    static List<Integer> find(TreeNode root,List<Integer> li){
        if(root==null){
            return li;
        }
            li.add(root.val);
        find(root.left,li);
         find(root.right,li);
        return li;
    }
    public boolean isSameTree(TreeNode p, TreeNode q) {
        List<Integer> li=new ArrayList<>();
        List<Integer> al=new ArrayList<>();
        List<Integer> lip=find(p,li);
        List<Integer> liq=find(q,al);
        if(lip.size()!=liq.size()){
            return false;
        }
        for(int i=0;i<lip.size();i++){
            if(lip.get(i)!=liq.get(i)){
                return false;
            }
        }
        return true;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(2n)

# Optimal Approach

```
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p==null && q==null){
            return true;
        }
        if(p==null || q==null){
            return false;
        }
        if(p.val!=q.val){
            return false;
        }
        return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(h)
