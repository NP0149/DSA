# Max Heap

[Problem Link](https://www.geeksforgeeks.org/problems/max-heap-implementation/1)


```
class maxHeap {
    public ArrayList<Integer> heap;
    // Constructor
    public maxHeap() {
        // Initialize your data members
        heap=new ArrayList<>();
    }
   public void swap(int parent,int child){
        int temp=heap.get(parent);
        heap.set(parent,heap.get(child));
        heap.set(child,temp);
        return;
    }
  public void heapify_up(int x,int i){
      while(i>0){
          int parent=(i-1)/2;
          if(heap.get(parent)>=heap.get(i)){
              break;
          }
          swap(parent,i);
          i=parent;
      }
      return;
   }
    public void push(int x) {
        // Insert x into the heap
        heap.add(x);
        heapify_up(x,heap.size()-1);
    }
 public void heapify_down(int i){
     int n=heap.size();
     while(true){
         int left=2*i+1;
         int right=2*i+2;
         int maxi=i;
         if(left<n && heap.get(left)>heap.get(maxi)){
             maxi=left;
         }
         if(right<n && heap.get(right)>heap.get(maxi)){
             maxi=right;
         }
         if(maxi==i){
             break;
         }
         swap(i,maxi);
         i=maxi;
     }
     
 }
    public void pop() {
        // Remove the top (maximum) element
        if(heap.isEmpty()){
            return ;
        }
        
        if (heap.size() == 1) {
        heap.remove(0);
        return;
        }
        int max=heap.get(0);
        int last=heap.get(heap.size()-1);
        heap.remove(heap.size()-1);
        heap.set(0,last);
        heapify_down(0);
        return;
    }

    public int peek() {
        // Return the top element or -1 if empty
        if(!heap.isEmpty()){
            return heap.get(0);
        }
        return -1;
    }

    public int size() {
        // Return the number of elements in the heap
        return heap.size();
    }
}
```

# Complexity Analysis

## Time
push:O(log n)

Pop:O(log n)

peek:O(1)

Size:O(1)
## Space:O(n)
