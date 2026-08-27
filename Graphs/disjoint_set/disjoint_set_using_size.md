# disjoint set using size

```
import java.util.*;

class disjoint{
    List<Integer> size=new ArrayList<>();
    List<Integer> parent=new ArrayList<>();
    disjoint(int n){
    for(int i=0;i<n;i++){
        size.add(1);
        parent.add(i);
    }
    }
    public int findupar(int node){
        if(node==parent.get(node)){
            return node;
        }
        int parentnode=findupar(parent.get(node));
        parent.set(node,parentnode);
        return parent.get(node);
    }

    public void union_by_size(int u,int v){
        int up=findupar(u);
        int vp=findupar(v);
        if(up==vp){
            return;
        }
        else if(size.get(up)>size.get(vp)){
            parent.set(vp,up);
        }
        else if(size.get(up)<size.get(vp)){
            parent.set(up,vp);
        }
        else{
            parent.set(up,vp);
            size.set(vp,size.get(vp)+1);
        }

    }


}

class m{
    public static void main(String args[]){
        disjoint ds=new disjoint(8);
        ds.union_by_size(1,2);
        ds.union_by_size(2,3);
        ds.union_by_size(4,5);
        ds.union_by_size(6,7);
        ds.union_by_size(5,6);
        if(ds.findupar(3)==ds.findupar(7)){
            System.out.println("same");
        }
        else{
            System.out.println("not same");
        }
        ds.union_by_size(3,7);
        if(ds.findupar(3)==ds.findupar(7)){
            System.out.println("same");
        }
        else{
            System.out.println("not same");
        }
    }

}

```
