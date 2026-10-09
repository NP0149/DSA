# Optimised

[Problem Link](https://www.geeksforgeeks.org/problems/print-anagrams-together/1)


```
class Solution {
    public ArrayList<ArrayList<String>> anagrams(String[] arr) {
        // code here
        HashMap<String,ArrayList<String>> hm=new HashMap<>();
        for(String s:arr){
            int freq[]=new int[26];
            for(char ch:s.toCharArray()){
                freq[ch-'a']++;
            }
            StringBuilder sb=new StringBuilder();
            for(int count:freq){
                sb.append('#').append(count);
            }
            String key=sb.toString();
            hm.putIfAbsent(key,new ArrayList<>());
            hm.get(key).add(s);
        }
        return new ArrayList<>(hm.values());
    }
}
```





```
class Solution {
    boolean find(String s,String t){
        char s1[]=s.toCharArray();
        char s2[]=t.toCharArray();
        Arrays.sort(s1);
        Arrays.sort(s2);
        if(s1.length!=s2.length){
            return false;
        }
        for(int i=0;i<s1.length;i++){
            if(s1[i]!=s2[i]){
                return false;
            }
        }
        return true;
    }
    public List<List<String>> groupAnagrams(String[] str) {
        int visited[]=new int[str.length];
        List<List<String>> ans=new ArrayList<>();
        for(int i=0;i<str.length;i++){
            if(visited[i]!=1){
                List<String> li=new ArrayList<>();
                li.add(str[i]);
                for(int j=i+1;j<str.length;j++){
                    if(visited[j]!=1){
                    if(find(str[i],str[j])){
                        visited[i]=1;
                        visited[j]=1;
                        li.add(str[j]);
                    }
                    }
                }
                ans.add(li);
            }
        }
        return ans;
    }
}
```
