# Number of provinces

```
class Solution {
    static void dfs(List<List<Integer>> li,int indx,boolean visited[]){
        visited[indx]=true;
        List<Integer> childs=li.get(indx);
        for(int num:childs){
            if(!visited[num]){
                dfs(li,num,visited);
            }
        }
    }
    public int findCircleNum(int[][] arr) {
       List<List<Integer>>li=new ArrayList<>();
       for(int i=0;i<arr.length;i++){
        li.add(new ArrayList<>());
       }
       for(int i=0;i<arr.length;i++){
        for(int j=0;j<arr[0].length;j++){
            if(arr[i][j]==1){
               li.get(i).add(j);
               li.get(j).add(i);
            }
        }
       }
       int count=0;
       boolean visited[]=new boolean[arr.length];
       for(int i=0;i<arr.length;i++){
         if(!visited[i]){
            count++;
            dfs(li,i,visited);
         }
       }
       return count;
    }
}
```
