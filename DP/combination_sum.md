[Problem Link](https://takeuforward.org/practice/dsa/combination-sum)


```
class Solution {
    List<List<Integer>> ans;
    void find(int arr[],int target,List<Integer> li,int indx){
       if(target==0){
         ans.add(new ArrayList<>(li));
         return;
       }
       if(indx<0){
        return;
       }
       if(target<0){
        return;
       }
       if(arr[indx]<=target){
        li.add(arr[indx]);
        find(arr,target-arr[indx],li,indx);
        li.remove(li.size()-1);
       }
       find(arr,target,li,indx-1);
    }
    public List<List<Integer>> combinationSum(int[] arr, int target) {
        //your code goes here
        ans=new ArrayList<>();
        List<Integer> li=new ArrayList<>();
        find(arr,target,li,arr.length-1);
        return ans;
    }
}
```
