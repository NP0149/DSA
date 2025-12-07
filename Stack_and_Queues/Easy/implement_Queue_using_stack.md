# Implement Queue using Stack

[Problem Link](https://leetcode.com/problems/implement-queue-using-stacks/)

```

class MyQueue {
    Stack<Integer> st;
    Stack<Integer> temp;
    public MyQueue() {
        st=new Stack<>();
        temp=new Stack<>();
    }
    
    public void push(int x) {
       while(!st.isEmpty()){
        temp.push(st.pop());
       }
       temp.push(x);
       while(!temp.isEmpty()){
        st.push(temp.pop());
       }
    }
    
    public int pop() {
        if(empty()){
            return -1;
        }
        else{
            return st.pop();
        }
    }
    
    public int peek() {
        if(empty()){
            return -1;
        }
        else{
            int x=st.peek();
            return x;
        }
    }
    
    public boolean empty() {
        return st.isEmpty();
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```

# Complexity Analysis

Time:O(n)

Space:O(n)
