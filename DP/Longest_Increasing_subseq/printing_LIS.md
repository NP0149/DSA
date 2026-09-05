# Printing longest increasing subsequence

[Problem Link](https://www.geeksforgeeks.org/problems/printing-longest-increasing-subsequence/1)


# Recurrsion

```
class Solution {
    
    static int maxlen;
    void find(int arr[],int indx,int prev,ArrayList<Integer> li,ArrayList<Integer> ans){
        if(indx>=arr.length){
            if(maxlen<li.size()){
                maxlen=li.size();
                ans.clear();
                ans.addAll(li);
            }
            return;
        }
        if(prev==-1 || arr[indx]>arr[prev]){
            li.add(arr[indx]);
            find(arr,indx+1,indx,li,ans);
            li.remove(li.size()-1);
        }
        find(arr,indx+1,prev,li,ans);
    }
    public ArrayList<Integer> getLIS(int arr[]) {
        maxlen=0;
       ArrayList<Integer> li=new ArrayList<>();
       ArrayList<Integer> ans=new ArrayList<>();
       find(arr,0,-1,li,ans);
       return ans;
    }
}

```
