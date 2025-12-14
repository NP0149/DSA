# Sliding window maximum

[Problem Link](https://leetcode.com/problems/sliding-window-maximum/)

# Brute

```
class Solution {
    static int find_max(List<Integer> li){
        int max=Integer.MIN_VALUE;
        for(int i=0;i<li.size();i++){
            max=Math.max(max,li.get(i));
        }
        return max;
    }
    public int[] maxSlidingWindow(int[] arr, int k) {
        List<Integer> li=new ArrayList<>();
        List<Integer> al=new ArrayList<>();
        for(int i=0;i<arr.length;i++){
            li.add(arr[i]);
            if(li.size()>k){
                li.remove(0);
            }
            if(li.size()==k){
             al.add(find_max(li));
            }
        }
        int ans[]=new int[al.size()];
        for(int i=0;i<al.size();i++){
            ans[i]=al.get(i);
        }
        return ans;
    }
}
```

# Complexity Analysis

Time:O(n X k)

Space:O(n)

# Optimal Approach

```
class Solution {
    public int[] maxSlidingWindow(int[] arr, int k) {
        List<Integer> li=new ArrayList<>();
        Deque<Integer> dq=new ArrayDeque<>();
        for(int i=0;i<arr.length;i++){
            if(!dq.isEmpty() && dq.peekFirst()<=i-k){
                dq.removeFirst();
            }
            while(!dq.isEmpty() && arr[dq.peekLast()]<arr[i]){
                dq.removeLast();
            }
            dq.addLast(i);
            if(i>=k-1){
                li.add(arr[dq.peekFirst()]);
            }
        }
        int ans[]=new int[li.size()];
        for(int i=0;i<li.size();i++){
            ans[i]=li.get(i);
        }
        return ans;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
