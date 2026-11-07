# sum of all subsets


```
class Solution {
    void find(int arr[],int indx,List<Integer> li,int sum){
        if(indx==arr.length){
            li.add(sum);
            return;
        }
        find(arr,indx+1,li,sum+arr[indx]);
        find(arr,indx+1,li,sum);
    }
    public List<Integer> subsetSums(int[] arr) {
      List<Integer> li=new ArrayList<>();
      find(arr,0,li,0);
      Collections.sort(li);
      return li;
    }
}
```
