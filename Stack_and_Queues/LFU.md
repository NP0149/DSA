# LFU cache

```
import java.util.*;

public class LFU {

    static class Node{
        int key;
        int value;
        int freq;

        Node next;
        Node prev;

        Node(int key,int value){
            this.key=key;
            this.value=value;
            this.freq=1;
        }
    }
    static class doublyll{
        Node head;
        Node tail;
        doublyll(){
            head=new Node(0,0);
            tail=new Node(0,0);
            head.next=tail;
            tail.prev=head;
        }
        void addfirst(Node node){
            node.next=head.next;
            node.prev=head;
            head.next.prev=node;
            head.next=node;
        }
        void remove(Node node){
            node.prev.next=node.next;
            node.next.prev=node.prev;
        }
        Node removelast(){
            if(head.next==tail){
                return null;
            }
            Node node=tail.prev;
            remove(node);
            return node;
        }
        boolean isEmpty(){
            return head.next==tail;
        }

    }

    static class LFUcache {
        int capacity;
        int minfreq;
        HashMap<Integer, Node> keymap;
        HashMap<Integer, doublyll> freqmap;

        LFUcache(int capacity) {
            this.capacity = capacity;
            this.minfreq = 0;
            keymap = new HashMap<>();
            freqmap = new HashMap<>();
        }

        public int get(int key) {
            if (!keymap.containsKey(key)) {
                return -1;
            }
            Node node = keymap.get(key);
            increasefreq(node);
            return node.value;
        }

        public void put(int key, int value) {
            if (capacity == 0) {
                return;
            }
            if (keymap.containsKey(key)) {
                Node node = keymap.get(key);
                node.value = value;
                increasefreq(node);
                return;
            }
            if (keymap.size() == capacity) {
                doublyll list = freqmap.get(minfreq);
                Node removenode = list.removelast();
                keymap.remove(removenode.key);
            }

            Node newnode = new Node(key, value);

            keymap.put(key, newnode);
            if (!freqmap.containsKey(1)) {
                freqmap.put(1, new doublyll());
            }

            freqmap.get(1).addfirst(newnode);
            minfreq = 1;
        }

        private void increasefreq(Node node) {
            int oldfreq = node.freq;
            doublyll oldlist = freqmap.get(oldfreq);
            oldlist.remove(node);
            if (oldfreq == minfreq && oldlist.isEmpty()) {
                minfreq++;
            }
            node.freq++;
            int newfreq = node.freq;
            if (!freqmap.containsKey(newfreq)) {
                freqmap.put(newfreq, new doublyll());
            }
            freqmap.get(newfreq).addfirst(node);
        }
    }
        public static void main(String args[]){
            LFUcache cache=new LFUcache(2);
            cache.put(1,10);
            cache.put(2,20);
            System.out.println(cache.get(1));
            cache.put(3,30);
            System.out.println(cache.get(2));
            System.out.println(cache.get(3));
            cache.put(4,40);
            System.out.println(cache.get(1));
            System.out.println(cache.get(3));
            System.out.println(cache.get(4));
        }



    }
```
