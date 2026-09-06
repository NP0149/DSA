[Problem Link](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering--170645/1)


```
class Solution {
    public int maxFruits(ArrayList<Integer> li, int m) {
       for(int i=0;i<m-1;i++){
           li.add(li.get(i));
       }
       int l=0;
       int sum=0;
       int maxsum=Integer.MIN_VALUE;
       for(int i=0;i<li.size();i++){
           sum+=li.get(i);
           if(i-l+1>m){
               sum-=li.get(l);
               l++;
           }
           if(i-l+1==m){
               maxsum=Math.max(maxsum,sum);
           }
       }
       return maxsum;
    }
}
```
