[Problem Link](https://takeuforward.org/practice/dsa/kth-smallest-and-largest-element-in-bst)

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
    void inorder(TreeNode root,List<Integer> li){
        if(root==null){
            return;
        }
        inorder(root.left,li);
        li.add(root.data);
        inorder(root.right,li);
    }
    public List<Integer> kLargesSmall(TreeNode root, int k) {
        //your code goes here
        List<Integer> li=new ArrayList<>();
        inorder(root,li);
        PriorityQueue<Integer> pq=new PriorityQueue<>();
        for(int i=0;i<li.size();i++){
             pq.add(li.get(i));
            if(pq.size()>k){
                pq.poll();
            }
        }
        int largest=pq.peek();
        pq=new PriorityQueue<>(Collections.reverseOrder());
       for(int i=0;i<li.size();i++){
        pq.add(li.get(i));
         if(pq.size()>k){
            pq.poll();
         }
       }
       int smallest=pq.peek();
       List<Integer> ans=new ArrayList<>();
       ans.add(smallest);
       ans.add(largest);
       return ans;
    }
}
```
