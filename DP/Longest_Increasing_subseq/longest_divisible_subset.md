# Longest divisible subset

[Problem Link](https://leetcode.com/problems/largest-divisible-subset/submissions/2131786919/)


```
class Solution {
    static int maxlen;
       void find(int arr[],int indx,int prev,List<Integer> li,List<Integer> ans){
        if(indx>=arr.length){
            if(maxlen<li.size()){
                maxlen=li.size();
                ans.clear();
                ans.addAll(li);
            }
            return;
        }
        if(prev==-1 || arr[indx]%arr[prev]==0){
            li.add(arr[indx]);
            find(arr,indx+1,indx,li,ans);
            li.remove(li.size()-1);
        }
        find(arr,indx+1,prev,li,ans);
       }
    public List<Integer> largestDivisibleSubset(int[] arr) {
        maxlen=0;
        Arrays.sort(arr);
        List<Integer> li=new ArrayList<>();
        List<Integer> ans=new ArrayList<>();
        find(arr,0,-1,li,ans);
        return ans;
    }
}
```
