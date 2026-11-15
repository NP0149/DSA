[Problem Link](https://takeuforward.org/practice/dsa/number-of-greater-elements-to-the-right)


```
class Solution {
    public List<Integer> count_NGE(int[] arr, int[] brr) {
        // Your code goes here
        int ans[]=new int[arr.length];
        for(int i=0;i<arr.length;i++){
            int count=0;
            for(int j=arr.length-1;j>i;j--){
               if(arr[j]>arr[i]){
                count++;
               }
            }
            ans[i]=count;
        }
        List<Integer> li=new ArrayList<>();
       for(int i=0;i<brr.length;i++){
        li.add(ans[brr[i]]);
       }
        return li;
    }
}
```
