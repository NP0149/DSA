# distance via every node to that particular node


```
class Solution {
    public void floydWarshall(int[][] arr) {
       for(int k=0;k<arr.length;k++){
           for(int i=0;i<arr.length;i++){
               for(int j=0;j<arr.length;j++){
                   if(arr[i][k]!=(int)1e8 && arr[k][j]!=(int)1e8){
                   arr[i][j]=Math.min(arr[i][j],arr[i][k]+arr[k][j]);
                   }
               }
           }
       }
    }}
```
