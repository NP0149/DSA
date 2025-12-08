# Implement Queue using linked list

[Problem Link](https://www.geeksforgeeks.org/problems/implement-queue-using-linked-list/1)

```
// Node class
class Node {
    int data;
    Node next;

    Node(int new_data) {
        data = new_data;
        next = null;
    }
}

// Queue class
class myQueue {
 private Node front;
 private Node rear;
 private int size;
    public myQueue() {
        // Initialize your data members
        front=rear=null;
        size=0;
        
    }

    public boolean isEmpty() {
        // check if the queue is empty
        return front==null;
    }

    public void enqueue(int x) {
        // Adds an element x at the rear of the queue.
        Node temp=new Node(x);
        if(isEmpty()){
            front=rear=temp;
        }
        else{
            rear.next=temp;
            rear=temp;
        }
        size++;
    }

    public void dequeue() {
        // Removes the front element of the queue
        if(isEmpty()){
            return;
        }
        else{
            front=front.next;
        }
        size--;
    }

    public int getFront() {
        // Returns the front element of the queue.
        // If queue is empty, return -1.
        if(isEmpty()){
            return -1;
        }
        else{
            return front.data;
        }
    }

    public int size() {
        // Returns the current size of the queue.
        return size;
    }
}
```

# Complexity Analysis

Time:O(1)

Space:O(n)
