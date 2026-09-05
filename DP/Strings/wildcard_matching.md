# Wildcard matching

# Recurrsive

```
class Solution {
    boolean find(String s,String t,int indx1,int indx2){
        if(indx1<0 && indx2<0){
            return true;
        }
        if(indx1<0 && indx2>=0){
            for(int i=indx2;i>=0;i--){
                if(t.charAt(i)!='*'){
                    return false;
                }
            }
            return true;
        }
        if(indx2<0){
            return false;
        }
        if(t.charAt(indx2)=='*'){
           return (find(s,t,indx1-1,indx2) || find(s,t,indx1,indx2-1));
        }
        if(s.charAt(indx1)==t.charAt(indx2) || t.charAt(indx2)=='?'){
            return find(s,t,indx1-1,indx2-1);
        }
       return false;
    }
    public boolean isMatch(String s, String t) {
        return find(s,t,s.length()-1,t.length()-1);
    }
}
```
