[Problem Link](https://www.geeksforgeeks.org/problems/the-celebrity-problem/1)


## he should know no one and all should know him

```
class Solution {
    public int celebrity(int arr[][]) {
       int knowsme[]=new int[arr.length];
       int iknow[]=new int[arr.length];
       for(int i=0;i<arr.length;i++){
           for(int j=0;j<arr.length;j++){
               if(i==j){
                   continue;
               }
               if(arr[i][j]==1){
                   knowsme[j]++;
                   iknow[i]++;
               }
           }
       }
       int celeb=-1;
       for(int i=0;i<arr.length;i++){
           if(knowsme[i]==arr.length-1 && iknow[i]==0){
               celeb=i;
           }
       }
       return celeb;
    }
}
```
