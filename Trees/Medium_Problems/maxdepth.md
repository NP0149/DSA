# Maxdepth of a tree

[Problem Link](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

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
    public int maxDepth(TreeNode root) {
        if(root==null){
            return 0;
        }
        int lh=maxDepth(root.left);
        int rh=maxDepth(root.right);
        return 1+Math.max(lh,rh);
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)


# Approach-II

```
class Solution {
    public int maxDepth(TreeNode root) {
      Queue<TreeNode> q=new LinkedList<>();
      List<List<Integer>> li=new ArrayList<>();
      if(root==null){
        return 0;
      }
      q.offer(root);
     while(!q.isEmpty()){
    int n=q.size();
    List<Integer> al=new ArrayList<>();
    for(int i=0;i<n;i++){
        if(q.peek().left!=null){
            q.offer(q.peek().left);
        }
        if(q.peek().right!=null){
            q.offer(q.peek().right);
        }
     al.add(q.poll().val);
    }
    li.add(al);
      }
      return li.size();
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)

# Approach-III

```
class Solution {
    public int maxDepth(TreeNode root) {
      Queue<TreeNode> q=new LinkedList<>();
      if(root==null){
        return 0;
      }
      q.offer(root);
      int depth=0;
     while(!q.isEmpty()){
    int n=q.size();
     
    for(int i=0;i<n;i++){
        if(q.peek().left!=null){
            q.offer(q.peek().left);
        }
        if(q.peek().right!=null){
            q.offer(q.peek().right);
        }
        q.poll();
    }
       depth++;
      }
      return depth;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)//best case O(n)//worst case
