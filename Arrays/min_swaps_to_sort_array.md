[Problem Link](https://www.geeksforgeeks.org/problems/minimum-swaps/1)


## remember that always sort only the temperarory 2D array only

```
class Solution {
    public int minSwaps(int arr[]) {
        // Code here
        int temp[][]=new int[arr.length][2];
        for(int i=0;i<arr.length;i++){
            temp[i][0]=arr[i];
            temp[i][1]=i;
        }
        Arrays.sort(temp,(a,b)->Integer.compare(a[0],b[0]));
        int swaps=0;
        boolean visited[]=new boolean[arr.length];
        for(int i=0;i<arr.length;i++){
            if(visited[i]==true || temp[i][1]==i){
             continue;
            }
            int j=i;
            int cycle=0;
            while(!visited[j]){
                visited[j]=true;
                j=temp[j][1];
                cycle++;
            }
            swaps+=cycle-1;
        }
        return swaps;
    }
}
```
