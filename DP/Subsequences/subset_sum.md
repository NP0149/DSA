# Subset Sum equal to target 

# Approach-I(Recurrsion)

```
import java.util.*;
public class generate_subsets {
    static void find_subsets(int arr[],int i,int n,List<Integer>li,int target,int sum){
        if(sum==target){
            System.out.println(li);
            return;
        }
        if(i>=n){
            return;
        }

        li.add(arr[i]);
        sum+=arr[i];
        find_subsets(arr,i+1,n,li,target,sum);
       int val= li.remove(li.size()-1);
       sum-=val;
        find_subsets(arr,i+1,n,li,target,sum);
    }

    public static void main(String[] args) {
        int arr[]={3,1,2};
        List<Integer> li=new ArrayList<>();
        int n=arr.length;
        int target=3;
        find_subsets(arr,0,n,li,target,0);
    }
}
```
# Complexity Analysis

Time:O(2^n) //2 times calling the same function in function

Space:O(n) //recurrsive stack
