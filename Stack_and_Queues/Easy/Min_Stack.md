# Min Stack

[Problem Link](https://leetcode.com/problems/min-stack/)

# Approach-I

```
class MinStack {
   private Stack<Pair<Integer,Integer>> st;
    public MinStack() {
        st=new Stack<>();
    }
    
    public void push(int val) {
        if(st.isEmpty()){
            st.push(new Pair<>(val,val));
        }
        else{
            Pair<Integer,Integer> top=st.peek();
            int get=top.getValue();
            st.push(new Pair<>(val,Math.min(get,val)));
        }
    }
    
    public void pop() {
        if(!st.isEmpty()){
            st.pop();
        }
       return;
    }
    
    public int top() {
        if(!st.isEmpty()){
             Pair<Integer,Integer> top=st.peek();
             return top.getKey();
        }
        return -1;
    }
    
    public int getMin() {
        if(!st.isEmpty()){
             Pair<Integer,Integer> top=st.peek();
             return top.getValue();
        }
        return -1;
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```

# Complexity Analysis

Time:O(1)

Space:O(n)
