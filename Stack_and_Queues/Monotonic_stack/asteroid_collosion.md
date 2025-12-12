# Asteroid Collosion

[Problem Link](https://leetcode.com/problems/asteroid-collision/submissions/1853710972/)

```
class Solution {
    public int[] asteroidCollision(int[] arr) {
        int n=arr.length;
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<n;i++){
            if(arr[i]>0){
                st.push(arr[i]);
            }
            else{
                while(!st.isEmpty() && st.peek()>0 && st.peek()<(int)Math.abs(arr[i])){
                    st.pop();
                }
                   if(st.isEmpty() || st.peek()<0){
                    st.push(arr[i]);
                }
             else if(!st.isEmpty() && st.peek()==(int)Math.abs(arr[i])){
                    st.pop();
                    continue;
                }
            }
        }
        List<Integer> li=new ArrayList<>();
        while(!st.isEmpty()){
            li.add(st.pop());
        }
        Collections.reverse(li);
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
