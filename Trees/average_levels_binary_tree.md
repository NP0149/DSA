# average of levels of binary tree

[Problem Link](https://leetcode.com/problems/average-of-levels-in-binary-tree/?envType=study-plan-v2&envId=top-interview-150)

## just do the BFS traversal at every level consider the sum=0 and then add the sum and then at last add the division to arrayList
```
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> li=new ArrayList<>();
        if(root==null){
            return li;
        }
        Queue<TreeNode> q=new LinkedList<>();
        q.offer(root);
        while(!q.isEmpty()){
            double sum=0;
            int size=q.size();
            for(int i=0;i<size;i++){
                TreeNode node=q.poll();
                sum+=node.val;
                if(node.left!=null){
                    q.offer(node.left);
                }
                if(node.right!=null){
                    q.offer(node.right);
                }
            }
            li.add(sum/size);
        }
        return li;
    }
}
```
