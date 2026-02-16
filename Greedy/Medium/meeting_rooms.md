# Meeting rooms

[Problem Link](https://www.geeksforgeeks.org/problems/attend-all-meetings/1)


```
class Solution {
    static boolean canAttend(int[][] arr) {
        // code here
        Arrays.sort(arr,(a,b)->Integer.compare(a[0],b[0]));
        List<int[]> li=new ArrayList<>();
        int freetime=0;
        for(int a[]:arr){
            if(li.isEmpty()){
                li.add(new int[]{a[0],a[1]});
                freetime=a[1];
            }
            else{
                if(a[0]>=freetime){
                    li.add(new int[]{a[0],a[1]});
                    freetime=a[1];
                }
            }
        }
        if(li.size()==arr.length){
            return true;
        }
        return false;
    }
}
```

# Complexity Analysis

Time:O(nlog n)

Space:O(n)


```
class Solution {
    static boolean canAttend(int[][] arr) {
        // code here
        Arrays.sort(arr,(a,b)->Integer.compare(a[0],b[0]));
        int freetime=0;
        int count=0;
        for(int a[]:arr){
            if(count==0){
                count++;
                freetime=a[1];
            }
            else{
                if(a[0]>=freetime){
                   count++;
                    freetime=a[1];
                }
            }
        }
        if(count==arr.length){
            return true;
        }
        return false;
    }
}
```

# Complexity

Time:O(nlogn)

Space:O(1)
