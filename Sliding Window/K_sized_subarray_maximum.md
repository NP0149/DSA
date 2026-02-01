# K sized sub array maximum

[Problem Link](https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1)

# Brute Approach

```
class Solution {
    static int find(int end,int start,int arr[]){
        List<Integer> li=new ArrayList<>();
        for(int i=start;i<=end;i++){
            li.add(arr[i]);
        }
        Collections.sort(li);
        return li.get(li.size()-1);
    }
    public ArrayList<Integer> maxOfSubarrays(int[] arr, int k) {
        int l=0;
        ArrayList<Integer> ans=new ArrayList<>();
        for(int i=0;i<arr.length;i++){
            if(i-l>k-1){
                l++;
            }
            if(i-l==k-1){
              ans.add(find(i,l,arr));
            }
        }
        return ans;
        
    }
}

```
