# Implement Queue Using Array

[Problem Link](https://www.geeksforgeeks.org/problems/implement-queue-using-array/1)


```
class myQueue {

    // Constructor
    private int q[];
    private int capacity;
    private int size;
    public myQueue(int n) {
        // Define Data Structures
        capacity=n;
        q=new int[capacity];
        size=0;
    }

    public boolean isEmpty() {
       return size==0;
    }

    public boolean isFull() {
      return size==capacity;
    }

    public void enqueue(int x) {
        if(isFull()){
            return;
        }
        size++;
        q[size-1]=x;
    }

    public void dequeue() {
      if(isEmpty()){
          return;
      }
      for(int i=1;i<size;i++){
          q[i-1]=q[i];
      }
      size--;
    }

    public int getFront() {
       if(isEmpty()){
           return -1;
       }
       return q[0];
    }

    public int getRear() {
       if(isEmpty()){
           return -1;
       }
       return q[size-1];
    }
}

```

# Complexity Analysis

Time:O(1)

Space:O(capacity)
