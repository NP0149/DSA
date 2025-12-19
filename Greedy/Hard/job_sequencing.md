# Job sequencing 

[Problem Link](https://www.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1)

# Brute Force

```
class Solution {
    static class jobs{
        int deadline;
        int profit;
        jobs(int deadline,int profit){
            this.deadline=deadline;
            this.profit=profit;
        }
    }
    public ArrayList<Integer> jobSequencing(int[] deadline, int[] profit) {
        jobs job[]=new jobs[deadline.length];
        for(int i=0;i<job.length;i++){
            job[i]=new jobs(deadline[i],profit[i]);
        }
        Arrays.sort(job,(a,b)->Integer.compare(b.profit,a.profit));
     int maxdl=0;
     for(int i=0;i<deadline.length;i++){
         maxdl=Math.max(maxdl,deadline[i]);
     }
     int arr[]=new int[maxdl+1];
     for(int i=0;i<arr.length;i++){
         arr[i]=-1;
     }
     int maxprofit=0;
     int count=0;
        for(int i=0;i<job.length;i++){
            for(int j=job[i].deadline;j>=1;j--){
                if(arr[j]==-1){
                    count++;
                    arr[j]=i;
                    maxprofit+=job[i].profit;
                    break;
                }
            }
        }
        ArrayList<Integer> li=new ArrayList<>();
        li.add(count);
        li.add(maxprofit);
        return li;
    }
}
```

# Complexities

Time:O(n^2)


Space:O(n)

## the optimal approach will bewith the Disjoint set union in graphs
