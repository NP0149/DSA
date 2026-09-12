# Max product subsequence

[Problem Link](https://www.geeksforgeeks.org/problems/maximum-product4633/1)


```
class Solution {
    static int maxpro;
    static int K;
    void find(int arr[],int indx,List<Integer> li){
        if(indx>=arr.length){
            if(li.size()==K){
                int pro=1;
                for(int i=0;i<K;i++){
                    pro*=li.get(i);
                }
                maxpro=Math.max(maxpro,pro);
            }
            return;
        }
        li.add(arr[indx]);
        find(arr,indx+1,li);
        li.remove(li.size()-1);
        find(arr,indx+1,li);
    }
    public int maxProduct(int[] arr, int k) {
       maxpro=Integer.MIN_VALUE;
       K=k;
       
       List<Integer> li=new ArrayList<>();
       find(arr,0,li);
       return maxpro;
    }
}
```
