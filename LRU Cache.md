# LRU Cache
**Solution:** use the hashmap and double linked list to solve this problem. The hashmap is to store the key-Node pair, and in the Node theres linked list which gives them order to define the usage of the LRU.

**Time Complexity:** O(1)

**Space Complexity:** O(n)


```java
    class Node{
        Node next;
        Node prev;
        int key;
        int value;
        public Node(Node prev, Node next, int key, int value){
            this.key = key;
            this.value = value;
            this.next = next;
            this.prev = prev;
        }
    }
    private HashMap<Integer,Node> map;
    private int cur_cap;
    private Node head;     //most recent use
    private Node tail;     //least recent use
    
    //move the node to the head
    public void splice(Node node){
        //if the node is the head
        if(node==this.head){
            return ;
        }
        //if the node is the tail
        else if(node == this.tail){
            node.prev.next = null;
            this.tail = node.prev;
        }
        //the node is in the middle
        else{
            node.prev.next = node.next;
            node.next.prev = node.prev;
        }
        this.head.prev = node;
        node.prev = null;
        node.next = this.head;
        this.head = node;
        return;
    }
    
    public LRUCache(int capacity) {
        this.cur_cap = capacity;
        this.head = null;
        this.tail = this.head;
        map = new HashMap<Integer,Node>();
    }
    
    public int get(int key) {
        Node tempNode = map.get(key);
        //not in the map
        if(tempNode == null){
            return -1;
        }
        //in the map
        else{
            splice(tempNode);
            return tempNode.value;
        }
    }
    
    public void put(int key, int value) {
        Node tempNode = map.get(key);
        //not in the map then add it 
        if(tempNode == null){
            tempNode = new Node(null,this.head,key,value);
            if(this.head != null) this.head.prev = tempNode;
            this.head = tempNode;
            if(this.tail == null) this.tail = tempNode;
            map.put(key,tempNode);
            if(this.cur_cap > 0){
                //insert the node
                this.cur_cap--; 
            }
            else{
                //System.out.println(cur_cap);
                this.tail = this.tail.prev;
                map.remove(this.tail.next.key);
                this.tail.next = null;
            }
        }
        else{
            tempNode.value = value;
            splice(tempNode);
            return;
        }
        /*Node tmpp = this.head;
        while(tmpp != null){
            System.out.println(tmpp.key);
            tmpp = tmpp.next;
        }
        System.out.println();*/
    }
```