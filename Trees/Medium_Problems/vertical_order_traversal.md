[Problem Link](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

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
