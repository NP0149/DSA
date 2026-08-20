# Longest Increasing subsequence

# Brute

```
import java.util.*;
public class lis {
    static int maxlen=0;
    static boolean is_increasing(List<Integer> li){
        int i=0;
        while(i<li.size()-2) {
            if (li.get(i) > li.get(i + 1)){
                return false;
            }
            i++;
        }
        if(li.size()>2) {
            if (li.get(li.size() - 1) < li.get(li.size() - 2)) {
                return false;
            }
        }
        return true;
    }

    static void find(int []arr,List<Integer> li,List<Integer>ans,int indx,int end){
        if(indx>end) {
           if(is_increasing(li)){
               if(maxlen<li.size()){
                   maxlen=li.size();
                   ans.clear();
                   ans.addAll(li);
               }
               return;
           }
            return;
        }
         li.add(arr[indx]);
         find(arr,li,ans,indx+1,end);
         li.remove(li.size()-1);
         find(arr,li,ans,indx+1,end);
        }

    public static void main(String args[]){
        int arr[]={1,45,67,3,9,22,6,10,14};
        List<Integer> li=new ArrayList<>();
        List<Integer> ans=new ArrayList<>();
        int maxlen=0;
       find(arr,li,ans,0,arr.length-1);

        System.out.println(ans);
    }

}
```


# recusrrsion

```
class Solution {
    static int find_rec(int arr[],int indx,int prev){
        if(indx>=arr.length){
            return 0;
        }
    int len=find_rec(arr,indx+1,prev);
    if(prev==-1 || arr[indx]>arr[prev]){
        len=Math.max(len,1+find_rec(arr,indx+1,indx));
    }
    return len;
    }
    public int LIS(int[] arr) {
   return find_rec(arr,0,-1);
    }
}

```
