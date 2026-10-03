# Longest divisible subset

[Problem Link](https://leetcode.com/problems/largest-divisible-subset/submissions/2131786919/)


```
class Solution {
    List<Integer> ans=new ArrayList<>();
    void find(int arr[],int prev,int indx,List<Integer> li){
        if(indx>=arr.length){
            if(li.size()>ans.size()){
                ans=new ArrayList<>(li);
            }
            return;
        }
        if(prev==-1 || arr[prev]%arr[indx]==0 || arr[indx]%arr[prev]==0){
            li.add(arr[indx]);
            find(arr,indx,indx+1,li);
            li.remove(li.size()-1);
        }
        find(arr,prev,indx+1,li);
    }
    public List<Integer> largestDivisibleSubset(int[] arr) {
        List<Integer> li=new ArrayList<>();
        Arrays.sort(arr);
       find(arr,-1,0,li);
        return ans;
    }
}
```
