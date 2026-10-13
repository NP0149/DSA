# Adding ones


[Problem Link](https://www.geeksforgeeks.org/problems/adding-ones3628/1)


```
class Solution {
    public ArrayList<Integer> update(int n, int[] arr) {
       int ans[]=new int[n];
       for(int i:arr){
           if(i<=n){
               ans[i-1]++;
           }
       }
       for(int i=1;i<ans.length;i++){
           ans[i]+=ans[i-1];
       }
      ArrayList<Integer> li=new ArrayList<>();
      for(int i=0;i<ans.length;i++){
          li.add(ans[i]);
      }
      return li;
    }
}
```


# Complexity 

Time:O(N+K)

Space:O(N)
