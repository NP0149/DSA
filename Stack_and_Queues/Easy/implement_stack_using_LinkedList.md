# Implementing stack using linked list

[Problem Link](https://www.geeksforgeeks.org/problems/implement-stack-using-linked-list/1)

```
// Node class
/* class Node {
    int data;
    Node next;

    Node(int new_data) {
        data = new_data;
        next = null;
    }
} */

// Stack class
class myStack {
    private Node top;
    private int size;
    public myStack() {
        // Initialize your data members
        top=null;
        size=0;
    }

    public boolean isEmpty() {
        // check if the stack is empty
        return top==null;
    }

    public void push(int x) {
        // Adds an element x at the rear of the stack.
        Node newnode=new Node(x);
        newnode.next=top;
        top=newnode;
        size++;
    }

    public void pop() {
        // Removes the front element of the stack.
        top=top.next;
        size--;
    }

    public int peek() {
        // Returns the front element of the stack.
        // If stack is empty, return -1.
        if(isEmpty()){
            return -1;
        }
        return top.data;
    }

    public int size() {
        // Returns the current size of the stack.
      return size;
    }
}

```

# Complexity Analaysis

Time:O(1)

Space:O(n)
