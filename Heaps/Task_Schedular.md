# Task Schedular

[Problem Link](https://leetcode.com/problems/task-scheduler/description/)

```
class Solution {
      static boolean check(HashMap<Character,Integer> hm){
        for(char num:hm.keySet()){
            if(hm.get(num)!=0){
                return false;
            }
        }
        return true;
    }
    public int leastInterval(char[] tasks, int n) {
            HashMap<Character,Integer> hm=new HashMap<>();
    for(int i=0;i<tasks.length;i++){
        hm.put(tasks[i],hm.getOrDefault(tasks[i],0)+1);
    }
    List<Character> li=new ArrayList<>();
    while(!check(hm)){
     int k=n+1;
     for(char ch:hm.keySet()){
        if(hm.get(ch)>0){
        li.add(ch);
        hm.put(ch,hm.get(ch)-1);
        k--;
        }
     }
     for(int i=k;i>0;i--){
        li.add('O');
     }
    }
    for(int i=li.size()-1;i>=0;i--){
        if(li.get(i)=='O'){
            li.remove(i);
        }
        else{
            break;
        }
    }
    System.out.println(li);
  return li.size();
    }
}
```
