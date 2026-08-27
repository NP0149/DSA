# disjoint set

```
import java.util.*;
class disjointset{
    List<Integer> rank=new ArrayList<>();
    List<Integer> parent=new ArrayList<>();
    disjointset(int n){
        for(int i=0;i<n;i++) {
            rank.add(0);
            parent.add(i);
        }
    }
    public int findupar(int node){
        if(node==parent.get(node)){
            return node;
        }
        int ulp=findupar(parent.get(node));
        parent.set(node,ulp);
        return parent.get(node);
    }
    public void unionbyrank(int u,int v){
        int ulp=findupar(u);
        int vlp=findupar(v);
        if(ulp==vlp) return;
        if(rank.get(ulp)>rank.get(vlp)){
            parent.set(vlp,ulp);
        }
        else if(rank.get(ulp)<rank.get(vlp)){
            parent.set(ulp,vlp);
        }
        else{
            parent.set(ulp, vlp);
            rank.set(vlp, rank.get(vlp) + 1);
        }
    }


}

class main{
    public static void main(String args[]){
        disjointset ds=new disjointset(8);
        ds.unionbyrank(1,2);
        ds.unionbyrank(2,3);
        ds.unionbyrank(4,5);
        ds.unionbyrank(6,7);
        ds.unionbyrank(5,6);
    if(ds.findupar(3)==ds.findupar(7)){
        System.out.println("same");
    }
    else{
        System.out.println("not same");
    }
    ds.unionbyrank(3,7);
    if(ds.findupar(3)==ds.findupar(7)){
        System.out.println("same");
    }
    else{
        System.out.println("not same");
    }
    }
}

```
