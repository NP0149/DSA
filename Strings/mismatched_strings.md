[Problem Link](https://leetcode.com/contest/weekly-contest-527/problems/find-mismatched-segments-between-two-strings/description/)


```
class Solution {
    public List<List<String>> findMismatchedSegments(String s1, String s2) {
        List<List<String>> li=new ArrayList<>();
          StringBuilder sb1=new StringBuilder();
            StringBuilder sb2=new StringBuilder();
        for(int i=0;i<s1.length();i++){
            if(s1.charAt(i)!=s2.charAt(i)){
                sb1.append(s1.charAt(i));
                sb2.append(s2.charAt(i));
            }
            else{
                if(!sb1.isEmpty() && !sb2.isEmpty()){
                     List<String> al=new ArrayList<>();
                  al.add(sb1.toString());
                al.add(sb2.toString());
                li.add(al);
                sb1.setLength(0);
                sb2.setLength(0);
                }
            }
        }
         if(!sb1.isEmpty() && !sb2.isEmpty()){
                     List<String> al=new ArrayList<>();
                  al.add(sb1.toString());
                al.add(sb2.toString());
                li.add(al);
         }
        
     return li;
    }
}©leetcode
```
