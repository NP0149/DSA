[Problem Link](https://leetcode.com/problems/minimum-swaps-to-sort-by-digit-sum/submissions/2174392828/?envType=daily-question&envId=2026-10-17)



## I am finding the number sum in array and storing number and then sum adjacent and then sorting the array based on the sum if two sum is sum then considering smaller number

## then creating a hashmap and then storing the target indexes like where the number need to be placed and then applying 

## cycle detection code will detect cycle and then will add swaps+=cycle-1

# new approach

### just store like temp[number][sum of number][index]  sort this 2 d array and then detect cycle

```
class Solution {
    int find_sum(int n){
        int sum=0;
        while(n!=0){
            int rem=n%10;
            sum+=rem;
            n=n/10;
        }
        return sum;
    }
    public int minSwaps(int[] arr) {
        int temp[][]=new int[arr.length][3];
        for(int i=0;i<arr.length;i++){
            temp[i][0]=arr[i];
            temp[i][1]=find_sum(arr[i]);
            temp[i][2]=i;
        }
        Arrays.sort(temp,(a,b)->{
            if(a[1]!=b[1]) return Integer.compare(a[1],b[1]);
            return Integer.compare(a[0],b[0]);
        });
        int swaps=0;
        boolean visited[]=new boolean[arr.length];
        for(int i=0;i<arr.length;i++){
            if(visited[i] || temp[i][2]==i){
                continue;
            }
            int j=i;
            int cycle=0;
            while(!visited[j]){
                visited[j]=true;
                j=temp[j][2];
                cycle++;
            }
            swaps+=cycle-1;
        }
        return swaps;
    }
}
```
```
class Solution {
    int find_sum(int n){
        int sum=0;
        while(n!=0){
            int rem=n%10;
            sum+=rem;
            n=n/10;
        }
        return sum;
    }
    public int minSwaps(int[] arr) {
        int mat[][]=new int[arr.length][2];
        for(int i=0;i<arr.length;i++){
            mat[i][0]=arr[i];
            mat[i][1]=find_sum(arr[i]);
        }
        Arrays.sort(mat,(a,b)->{
           if(a[1]!=b[1]){
            return Integer.compare(a[1],b[1]);
           }
           return Integer.compare(a[0],b[0]);});
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<mat.length;i++){
            hm.put(mat[i][0],i);
        }
        int swaps=0;
        boolean visited[]=new boolean[arr.length];
        for(int i=0;i<arr.length;i++){
            if(visited[i]==true || hm.get(arr[i])==i){
                continue;
            }
            int cycle=0;
            int j=i;
            while(visited[j]!=true){
                visited[j]=true;
                j=hm.get(arr[j]);
                cycle++;
            }
            swaps+=cycle-1;
        }
        return swaps;
    }
}
```
