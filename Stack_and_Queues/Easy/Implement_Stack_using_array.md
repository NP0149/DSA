# Implementing stack using array

[Problem Link](https://www.geeksforgeeks.org/problems/implement-stack-using-array/1)

```
class myStack {
  private int stack[];
  private int capacity;
  private int top;
    public myStack(int n) {
        // Define Data Structures
        stack=new int[n];
        capacity=n;
        top=-1;
    }

    public boolean isEmpty() {
        // check if the stack is empty
        return top==-1;
    }

    public boolean isFull() {
        // check if the stack is full
        return top==capacity-1;
    }

    public void push(int x) {
        // Inserts x at the top of the stack
        if(isFull()){
            return;
        }
        top++;
        stack[top]=x;
    }

    public void pop() {
        // Removes an element from the top of the stack
        if(isEmpty()){
            return;
        }
        if(top>=0){
            top--;
        }
    }

    public int peek() {
        // Returns the top element of the stack
        if(isEmpty()){
            return -1;
        }
        return stack[top];
    }
}
```

# Complexity Analysis

Time:O(1)

Space:O(capacity) --> due to the creation of array
