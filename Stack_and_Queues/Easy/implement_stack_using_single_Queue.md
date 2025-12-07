# Implement stack using Single Queue

[Problem Link](https://www.geeksforgeeks.org/problems/stack-using-two-queues/1)

```
class myStack {
    Queue<Integer> q = new LinkedList<>();

    void push(int x) {
        // Inserts an element x at the top of the stack
        q.offer(x);
        for(int i=0;i<q.size()-1;i++){
            q.offer(q.poll());
        }
    }

    void pop() {
        // Removes an element from the top of the stack
        if(q.isEmpty()){
            return;
        }
        q.poll();
    }

    int top() {
        // Returns the top element of the stack
        // If stack is empty, return -1
        if(q.isEmpty()){
            return -1;
        }
        return q.peek();
    }

    int size() {
        // Returns the current size of the stack
        return q.size();
    }
}


```

# Complexity Analysis

Time:O(1)

space:O(n)
