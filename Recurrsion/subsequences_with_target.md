# Subsequences with target sum


# Approach-I

using global variable

```
// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.*;
class Main {
    static int count=0;
    static void find(int i,int n,int arr[],List<Integer> li,int sum,int target){
        if(i>=n){
            if(sum==target && count==0){
            System.out.println(li);
            count++;
            }
            return;
        }
        li.add(arr[i]);
        sum+=arr[i];
        find(i+1,n,arr,li,sum,target);
        li.remove(li.size()-1);
        sum-=arr[i];
        find(i+1,n,arr,li,sum,target);
    }
    public static void main(String[] args) {
       int arr[]={1,3,2,3,3};
       List<Integer> li=new ArrayList<>();
       int n=arr.length;
       int target=3;
       find(0,n,arr,li,0,target);
    }
}
```

## Complexity Analysis

Time:O(2^n)

Space:O(n)


# Aproach-II

In the above approach we have used used global variable but it is not allowed so we should not use

```
// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.*;
class Main {
    static boolean find(int i,int n,int arr[],List<Integer> li,int sum,int target){
        if(i>=n){
            if(sum==target){
            System.out.println(li);
            return true;
            }
            return false;
        }
        li.add(arr[i]);
        sum+=arr[i];
        if(find(i+1,n,arr,li,sum,target)==true){
            return true;
        }
        li.remove(li.size()-1);
        sum-=arr[i];
        if(find(i+1,n,arr,li,sum,target)==true){
            return true;
        }
        return false;
    }
    public static void main(String[] args) {
       int arr[]={1,3,2,3,3};
       List<Integer> li=new ArrayList<>();
       int n=arr.length;
       int target=3;
       find(0,n,arr,li,0,target);
    }
}
```
# Complexity Analysis

Time:O(2^n)


Space:O(n)
