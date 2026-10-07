# Beautiful subsets

[Problem Link](https://leetcode.com/problems/the-number-of-beautiful-subsets/description/)



```
class Solution {
    int count=0;
    void solve(int arr[],int k,int indx,HashSet<Integer> hs){
        if(indx>=arr.length){
            if(hs.size()>0){
            count++;
            }
            return;
        }
        solve(arr,k,indx+1,hs);
        if(!hs.contains(arr[indx]-k) && !hs.contains(arr[indx]+k)){
            hs.add(arr[indx]);
            solve(arr,k,indx+1,hs);
            hs.remove(arr[indx]);
        }
    }
    public int beautifulSubsets(int[] arr, int k) {
        Arrays.sort(arr);
        HashSet<Integer> hs=new HashSet<>();
        solve(arr,k,0,hs);
        return count;
    }
}
```
