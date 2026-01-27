# Shop in candy store

[Problem Link](https://www.geeksforgeeks.org/problems/shop-in-candy-store1145/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=bottom_sticky_on_article)

# Better

```
class Solution {
    public ArrayList<Integer> minMaxCandy(int[] arr, int n) {
     Deque<Integer> dq=new ArrayDeque<>();
     Arrays.sort(arr);
     for(int i=0;i<arr.length;i++){
         dq.offerLast(arr[i]);
     }
     int minsum=0;
     while(!dq.isEmpty()){
         minsum+=dq.removeFirst();
         int k=n;
         while(k>0){
         if(!dq.isEmpty()) dq.removeLast();
         k--;
         }
         
     }
     int maxsum=0;
     for(int i=0;i<arr.length;i++){
         dq.offerLast(arr[i]);
     }
       while(!dq.isEmpty()){
           maxsum+=dq.removeLast();
           int k=n;
             while(k>0){
         if(!dq.isEmpty()) dq.removeFirst();
         k--;
         }
       }
       ArrayList<Integer> li=new ArrayList<>();
       li.add(minsum);
       li.add(maxsum);
       return li;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)


# Optimised

```
class Solution {
    public ArrayList<Integer> minMaxCandy(int[] arr, int k) {
        // code her
        Arrays.sort(arr);
        int i=0;
        int n=arr.length;
        int j=n-1;
        int minsum=0;
        while(i<=j){
            minsum+=arr[i];
            i++;
            j=j-k;
        }
        int t=n-1;
        int m=0;
        int maxsum=0;
        while(m<=t){
            maxsum+=arr[t];
            t--;
            m=m+k;
        }
        ArrayList<Integer> li=new ArrayList<>();
        li.add(minsum);
        li.add(maxsum);
        return li;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)

