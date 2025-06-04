# Sort colors

[Problem Link](https://leetcode.com/problems/sort-colors/)

1)consider a hashmap and then key is value and then their occurances as value and then 

2) place the values of the array in that way by occurances

```
class Solution {
    public void sortColors(int[] arr) {
      HashMap<Integer,Integer> hm=new HashMap<>();
        int n=arr.length;
        for(int i=0;i<n;i++){
            if(hm.containsKey(arr[i])){
                int prev=hm.get(arr[i]);
                    hm.put(arr[i],prev+1);
                }
            else{
                hm.put(arr[i],1);
            }
        }
        int j=0;
        for(int num:hm.keySet()){
            for(int i=0;i<hm.get(num);i++){
                arr[j]=num;
                j++;
            }
        }
        }
    }
```

# Complexities

Time:O(n)

Space:O(1) //because always we are storing only 3 numbers(0,1,2) and their count so it becomes O(1)
