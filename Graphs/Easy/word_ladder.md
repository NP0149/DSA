# word ladder

```

class pair{
    String first;
    int steps;
    pair(String first,int steps){
        this.first=first;
        this.steps=steps;
    }
}

class Solution {
    public int ladderLength(String start, String end, List<String> words) {
        Queue<pair> q=new LinkedList<>();
         HashSet<String> hs=new HashSet<>();
         for(String str:words){
            hs.add(str);
         }
         q.offer(new pair(start,1));
         hs.remove(start);
         while(!q.isEmpty()){
            pair p=q.poll();
            String str=p.first;
            int steps=p.steps;
            if(str.equals(end)){
                return steps;
            }
            char strarr[]=str.toCharArray();
            for(int i=0;i<str.length();i++){
                char org=strarr[i];
                for(char ch='a';ch<='z';ch++){
                    strarr[i]=ch;
                    String changed=new String(strarr);
                    if(hs.contains(changed)){
                        hs.remove(changed);
                        q.offer(new pair(changed,steps+1));
                    }
                }
                strarr[i]=org;
            }
         }
         return 0;
    }
}
```
