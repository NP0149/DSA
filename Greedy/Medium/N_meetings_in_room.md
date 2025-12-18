# N meetings in a room

[Problem Link](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)

```
class Solution {
    static class interval{
        int start_time;
        int end_time;
        int indx;
        interval(int start,int end,int i){
           start_time=start;
           end_time=end;
           indx=i;
        }
    }
    public int maxMeetings(int start[], int end[]) {
        interval time[]=new interval[start.length];
        for(int i=0;i<start.length;i++){
            time[i]=new interval(start[i],end[i],i);
        }
        List<int[]> li=new ArrayList<>();
        Arrays.sort(time,(a,b)->Integer.compare(a.end_time,b.end_time));
        int freetime=0;
        for(interval inti:time){
         if(li.isEmpty()){
             li.add(new int[]{inti.start_time,inti.end_time,inti.indx});
             freetime=inti.end_time;
         }
         else if(inti.start_time>freetime){
               li.add(new int[]{inti.start_time,inti.end_time,inti.indx});
               freetime=li.get(li.size()-1)[1];
         }
        }
        return li.size();
    }
}

```

# Complexity Analysis

Time:O(nlogn)

Space:O(n)
