# Print root to leaf

[Problem Link](https://takeuforward.org/plus/dsa/problems/print-root-to-note-path-in-bt)

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
    static void find(TreeNode root,List<Integer> path,List<List<Integer>> result){
      if(root==null){
        return;
      }
         path.add(root.data);
      if(root.left==null && root.right==null){
        result.add(new ArrayList<>(path));
      }
      else{
        find(root.left,path,result);
        find(root.right,path,result);
      }
      path.remove(path.size()-1);
    }
    public List<List<Integer>> allRootToLeaf(TreeNode root) {
        List<List<Integer>> result=new ArrayList<>();
        List<Integer> path=new ArrayList<>();
       if(root==null){
        return result;
       }
       find(root,path,result);
       return result;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(h)
