# Merged mails

```
class dsu{
    private int[]rank;
    public int []parent;
    dsu(int v){
        rank=new int[v];
        parent=new int[v];
        for(int i=0;i<v;i++){
            rank[i]=0;
            parent[i]=i;
        }
    }
    public int find(int node){
        if(parent[node]!=node){
            return parent[node]=find(parent[node]);
        }
        return parent[node];
    }
    public void union(int x,int y){
        int p1=find(x);
        int p2=find(y);
        if(p1!=p2){
            if(rank[p1]>rank[p2]){
                parent[p2]=p1;
            }
            else if(rank[p1]<rank[p2]){
                parent[p1]=p2;
            }
            else{
                parent[p2]=p1;
                rank[p1]++;
            }
        }
    }
}
class Solution {
    public List<List<String>> accountsMerge(List<List<String>> li) {
        int n=li.size();
        dsu d=new dsu(n);
        HashMap<String,Integer> hm=new HashMap<>();
        for(int i=0;i<n;i++){
            for(int j=1;j<li.get(i).size();j++){
              String mail=li.get(i).get(j);
              if(!hm.containsKey(mail)){
                hm.put(mail,i);
              }
              else{
                d.union(i,hm.get(mail));
              }
            }
        }
       List<List<String>> merged=new ArrayList<>();
       for(int i=0;i<li.size();i++){
         merged.add(new ArrayList<String>());
       }
       for(HashMap.Entry<String,Integer> it:hm.entrySet()){
        String mail=it.getKey();
        int node=d.find(it.getValue());
        merged.get(node).add(mail);
       }
       List<List<String>> ans=new ArrayList<>();
       for(int i=0;i<n;i++){
        if(merged.get(i).size()==0) continue;
        Collections.sort(merged.get(i));
          List<String> temp=new ArrayList<>();
          temp.add(li.get(i).get(0));
          for(String mail:merged.get(i)){
            temp.add(mail);
          }
          ans.add(temp);
       }
       return ans;
    }
}
```
