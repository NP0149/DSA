# Stock Span Algorithm

[Problem Link](https://leetcode.com/problems/online-stock-span/)

# Optimal Approach-I

```
class StockSpanner {
  private Stack<int[]> st;
    public StockSpanner() {
        st=new Stack<>();
    }
    
    public int next(int price) {
       int span=1;
       while(!st.isEmpty() && st.peek()[0]<=price){
        span+=st.pop()[1];
       }
       st.push(new int[]{price,span});
       return span;
    }
}

/**
 * Your StockSpanner object will be instantiated and called as such:
 * StockSpanner obj = new StockSpanner();
 * int param_1 = obj.next(price);
 */
```
# Complexity Analysis

time:O(n)

Space:O(n)

# Another Approach

1)first we need to find the previous greater element ans then need to store it index and then the span becomes i-pge[i]+1


```

// Use this editor to write, compile and run your Java code online
import java.util.*;
class Main {
    static int[] find_pge(int arr[]){
        int pge[]=new int[arr.length];
        Stack<Integer> st=new Stack<>();
        for(int i=0;i<arr.length;i++){
            while(!st.isEmpty() && arr[st.peek()]<=arr[i]){
                st.pop();
            }
            if(st.isEmpty()){
                pge[i]=-1;
            }
            else{
                pge[i]=st.peek();
            }
            st.push(i);
        }
        return pge;
    }
    public static void main(String[] args) {
    int arr[]={7,2,1,3,3,1,8};
    int pge[]=find_pge(arr);
    int ans[]=new int[arr.length];
    for(int i=0;i<arr.length;i++){
        ans[i]=i-pge[i];
    }
    for(int i=0;i<ans.length;i++){
        System.out.print(ans[i]+"  ");
    }
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
