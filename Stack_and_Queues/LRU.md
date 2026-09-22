# LRU cache

```
import java.util.*;
class LRUCache{
    class Node{
        int key;
        int value;
        Node prev;
        Node next;
        Node(int key,int value){
            this.key=key;
            this.value=value;
        }
    }
    int capacity;
    HashMap<Integer,Node> map;
    Node head;
    Node tail;
    LRUCache(int capacity){
        this.capacity=capacity;
        map=new HashMap<>();
        head=new Node(0,0);
        tail=new Node(0,0);
        head.next=tail;
        tail.prev=head;
    }
    void remove(Node node){
        node.prev.next=node.next;
        node.next.prev=node.prev;
    }
    void addnode(Node node){
        node.prev=head;
        node.next=head.next;
        head.next.prev=node;
        head.next=node;
    }
    int get(int key){
        if(!map.containsKey(key)){
            return -1;
        }
        Node node=map.get(key);
        remove(node);
        addnode(node);
        return node.value;
    }
    void put(int key,int value){
        if(map.containsKey(key)){
            Node node=map.get(key);
            node.value=value;
            remove(node);
            addnode(node);
            return;
        }
        Node node=new Node(key,value);
        map.put(key,node);
        addnode(node);
        if(map.size()>capacity){
            Node rnode=tail.prev;
            remove(rnode);
            Node newnode=new Node(key,value);
            addnode(newnode);
        }
    }
    void display(){
        Node temp=head.next;
        while(temp!=tail){
            System.out.println(temp.key+" "+temp.value);
            temp=temp.next;
        }
    }


}

public class LRU{

    public static void main(String args[]){
   LRUCache lru=new LRUCache(3);
   lru.put(3,7);
   lru.put(2,6);
   lru.put(8,9);
        System.out.println(lru.get(3));
        lru.put(3,5);
        System.out.println(lru.get(3));
        System.out.println(lru.get(2));
    }
}

```
