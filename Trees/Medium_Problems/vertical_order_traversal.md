
[Problem Link](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

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
    class pair{
        TreeNode node;
        int row;
        int col;
        pair(int col,int row,TreeNode node){
            this.node=node;
            this.row=row;
            this.col=col;
        }
    }
    public List<List<Integer>> verticalTraversal(TreeNode root) {
        TreeMap<Integer,TreeMap<Integer,PriorityQueue<Integer>>> tm=new TreeMap<>();
        Queue<pair> q=new LinkedList<>();
       q.add(new pair(0,0,root));
       while(!q.isEmpty()){
        pair p=q.poll();
        int row=p.row;
        int col=p.col;
        TreeNode node=p.node;
        tm.putIfAbsent(col,new TreeMap<>());
        tm.get(col).putIfAbsent(row,new PriorityQueue<>());
        tm.get(col).get(row).add(node.val);
        if(node.left!=null){
            q.add(new pair(col-1,row+1,node.left));
        }
        if(node.right!=null){
            q.add(new pair(col+1,row+1,node.right));
        }
       }
       List<List<Integer>> ans=new ArrayList<>();
       for(TreeMap<Integer,PriorityQueue<Integer>> t:tm.values()){
          List<Integer> li=new ArrayList<>();
          for(PriorityQueue<Integer> pq:t.values()){
            while(!pq.isEmpty()){
                li.add(pq.poll());
            }
          }
          ans.add(li);
       }
       return ans;
    }
}
```

```
/* Structure of binary tree node
class Node {
    int data;
    Node left;
    Node right;

    Node(int val) {
        data = val;
        left = right = null;
    }
}*/

class Solution {
    class pair{
        Node node;
        int col;
        pair(Node node,int col){
            this.node=node;
            this.col=col;
        }
    }
    public ArrayList<ArrayList<Integer>> verticalOrder(Node root) {
        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
        Queue<pair> q=new LinkedList<>();
        q.add(new pair(root,0));
        TreeMap<Integer,ArrayList<Integer>> tm=new TreeMap<>();
        while(!q.isEmpty()){
            pair p=q.poll();
            Node node=p.node;
            int col=p.col;
            tm.putIfAbsent(col,new ArrayList<>());
            tm.get(col).add(node.data);
            if(node.left!=null){
                q.add(new pair(node.left,col-1));
            }
            if(node.right!=null){
                q.add(new pair(node.right,col+1));
            }
        }
        for(ArrayList<Integer> li:tm.values()){
            ans.add(li);
        }
        return ans;
    }
}

```
