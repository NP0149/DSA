# xor in k size

[Problem Link](https://www.geeksforgeeks.org/problems/count-distinct-elements-in-every-window/1)

# Brute Force

```
class Solution {
    static int find(List<Integer> li){
       Map<Integer,Integer> hm=new HashMap<>();
       for(int num:li){
           hm.put(num,hm.getOrDefault(num,0)+1);
       }
     return hm.size();
    }
    ArrayList<Integer> countDistinct(int arr[], int k) {
        // code here
        int l=0;
        int idx=0;
        ArrayList<Integer> ans=new ArrayList<>();
        List<Integer> li=new ArrayList<>();
        for(int i=0;i<arr.length;i++){
            li.add(arr[i]);
            if(i-l>k-1){
                li.remove(0);
                l++;
            }
            if(i-l==k-1){
               ans.add(find(li));
            }
        }
        return ans;
    }
}
```
# Complexity analysis

Time:O(nk)

Space:O(k)
