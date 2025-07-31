# Implement Stack Using queue

[Problem Link](https://leetcode.com/problems/implement-stack-using-queues/)

```
class MyStack {
     Queue<Integer> q;
    public MyStack() {
    q=new LinkedList<>();
    }
    
    public void push(int x) {
        q.add(x);
        for(int i=0;i<q.size()-1;i++){
            int temp=q.poll();
            q.add(temp);
        }
    }
    
    public int pop() {
        return q.poll();
    }
    
    public int top() {
        return q.peek();
    }
    
    public boolean empty() {
        return q.isEmpty();
    }
}
```

# Complexity Analysis

Time:

push:O(n)

pop:O(1)

peek:O(1)

isEmpty:O(1)

Space:O(n)
