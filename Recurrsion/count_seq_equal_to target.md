# Counting number of subsequences equal to the target

```
// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.*;
class Main {
    static int find(int i,int n,int arr[],List<Integer> li,int sum,int target){
        if(i>=n){
            if(sum==target){
            return 1;
            }
            return 0;
        }
        li.add(arr[i]);
        sum+=arr[i];
       int left=find(i+1,n,arr,li,sum,target);
        li.remove(li.size()-1);
        sum-=arr[i];
       int right=find(i+1,n,arr,li,sum,target);
        return left+right;
    }
    public static void main(String[] args) {
       int arr[]={1,3,2};
       List<Integer> li=new ArrayList<>();
       int n=arr.length;
       int target=3;
       int m=find(0,n,arr,li,0,target);
       System.out.println(m);
    }
}
```
