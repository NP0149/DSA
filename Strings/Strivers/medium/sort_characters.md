[Problem Link](https://leetcode.com/problems/sort-characters-by-frequency/)


```
class Solution {
    public String frequencySort(String s) {
        HashMap<Character,Integer> hm=new HashMap<>();
       for(int i=0;i<s.length();i++){
        char ch=s.charAt(i);
        hm.put(ch,hm.getOrDefault(ch,0)+1);
       }
        PriorityQueue<Map.Entry<Character,Integer>> pq=new PriorityQueue<>((a,b)->Integer.compare(b.getValue(),a.getValue()));
        pq.addAll(hm.entrySet());
        StringBuilder sb=new StringBuilder();
        while(!pq.isEmpty()){
            Map.Entry<Character,Integer> hm1=pq.poll();
            char ch=hm1.getKey();
            int num=hm1.getValue();
           for(int i=0;i<num;i++){
            sb.append(ch);
           }
        }
        return sb.toString();
    }
}
```
