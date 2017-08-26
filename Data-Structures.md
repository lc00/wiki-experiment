## Arrays

A linear collection of elements, where the elements can be access via indices.

## Lists

An ordered sequence of data.

* Uniform interface for interacting with the underlying data structure is when accessing elements
* You can update the list without also having to update the iterator (indexes in arrays become invalid easily)
* Good for when you don't care about the order or you don't have to search the list

### Components

* Element - Item in the list
* Empty List - No items
* Length - # of elements
* Append - Add to the end
* Insert - Add to the beginning
* Remove - Delete an element
* Clear - Remove all elements
* Front - Beginning of a list
* End - End of a list

### Implementation

```js
class List {
    constructor(){
        this.listSize = 0;
        this.position = 0;
        this.dataStore = [];
    }
    clear(){
        delete this.dataStore;
        this.dataStore = [];
        this.listSize = this.position = 0;
    }
    find(element){
        for (let i = 0; i < this.dataStore.length; ++i){
            if (this.dataStore[i] == element){
                return i;
            }
        }
        return -1;
    }
    toString(){
        return this.dataStore;
    }
    insert(element, after){
        var insertPosition = this.find(after);
        if (insertPosition > -1){
            this.dataStore.splice(insertPosition + 1, 0, element);
            ++this.listSize;
            return true;
        }
        return false;
    }
    append(element){
        this.dataStore[this.listSize++] = element;
    }
    remove(){
        var foundAt = this.find(element);
        if (foundAt > 1){
            this.dataStore.splice(foundAt, 1);
            --this.listSize;
            return true;
        }
        return false;
    }
    front(){
        this.position = 0;
    }
    end(){
        this.position = this.listSize - 1;
    }
    previous(){
        if (this.position > 0){
            --this.position;
        }
    }
    next(){
        if (this.position < this.listSize - 1){
            ++this.position;
        }
    }
    length(){
        return this.listSize;
    }
    currentPosition(){
        return this.position;
    }
    moveTo(position){
        this.position = position;
    }
    getElement(){
        return this.dataStore[this.position];
    }
    contains(){
        for (let i = 0; i < this.dataStore.length; ++i){
            if (this.dataStore[i] == element){
                return true;
            }
        }
        return false;
    }
}
```

### Iterating Through A list

```js
for (list.front(); list.currentPosition() < list.length(); list.next()){
    // list.getElement();
}
```

## Stacks

A list of elements that are accessible only from one end of the list.

* A LIFO
* Used for:
    * Expression evaluation
    * Handling function calls
    * Converting numbers from one base to another
    * Reversing strings
    * Palindromes
    * Implementing recursion

### Components

* Top = End of the stack
* Push - Adding an element
* Pop - Removing an element
* Peek - Show what's on top but don't remove it
* Length - How many elements
* Clear - Remove all elements

### Implementation

```js
class Stack {
    constructor(){
        this.dataStore = [];
        this.top = 0;
    }
    push(element){
        this.dataStore[this.top++] = element;
    }
    pop(){
        return this.dataStore[--this.top];
    }
    peek(){
        return this.dataStore[this.top - 1];
    }
    clear(){
        this.top = 0;
    }
    length(){
        return this.top;
    }
}
```

## Queues

A list where data is inserted at the end and removed from the front. Queues store data in the order the occur.

* A FIFO
* Used for:
    * Ordering submitted processes
    * Modeling lines of people, etc.
    * Radix sorts

### Components

* Enqueue - Add an item
* Dequeue - Remove an item
* Length - Count items
* Clear - Remove all items
* Peek - Show next item

### Implementation

```js
class Queue {
    constructor(){
        this.dataStore = [];
    }
    enqueue(element){
        this.dataStore.push(element);
    }
    dequeue(){
        return this.dataStore.shift();
    }
    front(){
        return this.dataStore[0];
    }
    back(){
        return this.dataStore.[this.dataStore.length - 1];
    }
    empty(){
        if (this.dataStore.length == 0){
            return true;
        } else {
            return false;
        }
    }
    toString(){
        var returnString = "";
        for (let i = 0; < i < this.dataStore.length; ++i){
            returnString += this.dataStore[i] + "\n";
        }
        return returnString;
    }
}
```

## Priority Queues

A queue where data doesn't have to be accessed in FIFO order.

* Used for:
    * Ordering submitted processes
    * Modeling triaged situations

### Components

* All elements of a queue
* Priority

### Implementation

```js
class Queue {
    constructor(){
        this.dataStore = [];
    }
    enqueue(element){
        this.dataStore.push(element);
    }
    dequeue(){
        var priority = this.dataStore[0].priority;
        for (let i = 1; < this.dataStore.length; ++i){
            if (this.dataStore[i].priority < priority){
                priority = i;
            }
        }
        return this.dataStore.splice(priority,1);
    }
    front(){
        return this.dataStore[0];
    }
    back(){
        return this.dataStore.[this.dataStore.length - 1];
    }
    empty(){
        if (this.dataStore.length == 0){
            return true;
        } else {
            return false;
        }
    }
    toString(){
        var returnString = "";
        for (let i = 0; < i < this.dataStore.length; ++i){
            returnString += this.dataStore[i] + "\n";
        }
        return returnString;
    }
}
```

## Linked Lists

A linked list a collection of nodes that have pointers to the next node in the list.

* Arrays have a fixed length in some languages, whereas linked lists don't
* Array indexes have to move around to accomodate insertions

### Components

* Node - Item in a linked list
* Head - Beginning of a linked list, often a special kind of node
* End of a linked list - Last node points to `null`
* Advance - Move forward `n` nodes
* Back - Move backward `n` nodes
* Show - Display the current node

### Used For:

* Every situation where a 1-dimensional array works, except not when you need random access to elements
* Insertion and deletion are really efficient, especially insertion 

### Implementation

```js
class Node {
    constructor(element){
        this.element = element;
        this.next = null;
    }
}

class LinkedList {
    constructor(){
        this.head = new Node("head");
    }
    find(item){
        var currentNode = this.head;
        while (currrentNode.element != item){
            currentNode = currentNode.next;
        }
        return currentNode;
    }
    insert(newElement, item){
        var newNode = new Node(newElement);
        var currentNode = this.find(item);
        newNode.next = currentNode.next;
        currentNode.next = newNode;
    }
    findPrevious(item){
        var currentNode = this.head;
        while (!(currentNode.next == null) && (currentNode.next.element != item)){
            currentNode = currentNode.next;
        }
        return currentNode;
    }
    remove(item){
        var previousNode = this.findPrevious(item);

        if (!(previousNode.next == null)){
            previousNode.next = previousNode.next.next;
        }
    }
    display(){
        var currentNode = this.head;
        while (!(currentNode.next == null)){
            print(currentNode.next.element);
            currentNode = currentNode.next;
        }
    }
}
```

### Doubly-Linked Lists

A doubly linked list a collection of nodes that have pointers to the next and previous nodes in the list.

* Possible to traverse backward
* Removal is more efficient than singly linked list, but insertion is slower

#### Implementation

```js
class Node {
    constructor(element){
        this.element = element;
        this.next = null;
        this.previous = null;
    }
}

class LinkedList {
    constructor(){
        this.head = new Node("head");
    }
    find(item){
        var currentNode = this.head;
        while (currrentNode.element != item){
            currentNode = currentNode.next;
        }
        return currentNode;
    }
    findLast(){
        var currentNode = this.head;
        while (!(currrentNode.next == null)){
            currentNode = currentNode.next;
        }
        return currentNode;
    }
    insert(newElement, item){
        var newNode = new Node(newElement);
        var currentNode = this.find(item);
        newNode.next = currentNode.next;
        newNode.previous = currentNode;
        currentNode.next = newNode;
    }
    remove(item){
        var currentNode = this.find(item);
        if (!(currentNode.next == null)){
            currentNode.previous.next = currentNode.next;
            currentNode.next.previous = currentNode.previous;
            currentNode.next = null;
            currentNode.previous = null;
        }
    }
    display(){
        var currentNode = this.head;
        while (!(currentNode.next == null)){
            print(currentNode.next.element);
            currentNode = currentNode.next;
        }
    }
    displayReverse(){
        var currentNode = this.head;
        currentNode = this.findLast();
        while (!(currentNode.previous == null)){
            print(currentNode.element);
            currentNode = currentNode.previous;
        }
    }
}
```

### Circularly Linked Lists

A circularly linked list is a singularly linked list that's end points back to its head.

* You can go backward through a list without needing to doubly link it

#### Implementation

```js
class Node {
    constructor(element){
        this.element = element;
        this.next = null;
        this.previous = null;
    }
}

class LinkedList {
    constructor(){
        this.head = new Node("head");
        this.head.next = this.head;
    }
    find(item){
        var currentNode = this.head;
        while (currrentNode.element != item){
            currentNode = currentNode.next;
        }
        return currentNode;
    }
    insert(newElement, item){
        var newNode = new Node(newElement);
        var currentNode = this.find(item);
        newNode.next = currentNode.next;
        newNode.previous = currentNode;
        currentNode.next = newNode;
    }
    remove(item){
        var currentNode = this.find(item);
        if (!(currentNode.next == null)){
            currentNode.previous.next = currentNode.next;
            currentNode.next.previous = currentNode.previous;
            currentNode.next = null;
            currentNode.previous = null;
        }
    }
    display(){
        var currentNode = this.head;
        while (!(currentNode.next == null) && !(currentNode.next.element == "head")){
            print(currentNode.next.element);
            currentNode = currentNode.next;
        }
    }
}
```

## Dictionaries

Stores data as key-value pairs.

### Components

* Add - Adds a new key/value pair
* Remove - Removes a key/value pair
* Find - Finds a value based on its key
* Show All - Show all keys and values
* Count - Number of key/value pairs
* Clear - Remove all pairs

### Implementation

```js
class Dictionary {
    constructor(){
        this.dataStore = [];
    }
    add(key, value){
        this.dataStore[key] = value;
    }
    find(key){
        return this.dataStore[key];
    }
    remove(key){
        delete this.dataStore[key];
    }
    showAll(){
        for each (var key in Object.keys(this.dataStore)){
            print(`${key} -> ${this.datastore[key]}`);
        }
    }
}
```

## Hash Table

* Have a limited number of array members
* Goal is to evenly distribute the keys between members of the array

### Components

* Sized array
    * Needs to be prime and bigger than 100
* Hashing function needs to account for collisions
    * Horner's method sums the ASCII values of a string, but then multiplies them by a prime constant
* Handling collisions:
    * Separate Chaining- Initialize every position in the hash table with an empty array and push items into it. Have to store the unhashed key along with the data in order to find it.
    * Linear Probing- When a collision is found, look for the next empty cell to store the data in. Space efficient. Works better when the array is large (array size is twice the size of the data to be stored). Works by storing keys and values separately, and when it doesn't find a match, it increments through the array until it finds a match.

### Used For

* Very fast insertion, deletion, and retrieval
* Bad at searching and sorting

### Implementation

```js
class HashTable {
    constructor(){
        this.table = new Array(137);
    }
    hornerHash(string, array){
        const PRIME_CONSTANT = 37;
        var total = 0;
        for (let i = 0; i < string.length; ++i){
            total += (PRIME_CONSTANT * total) + string.charCodeAt(i);
        }
        return parseInt(total % array.length);
    }
    showDistribution(){
        var n = 0;
        for (let i = 0; i < this.table.length; ++i){
            if (this.table[i] != undefined){
                print(`${i}: this.table[i]`);
            }
        }
    }
    put(key, data){
        var position = this.hornerHash(key, this.table);
        this.table[position] = data;
    }
    get(key){
        return this.table[this.hornerHash(key)];
    }
}
```

## Sets

A collection of unordered, unique elements.

### Components

* Members - Items in the set
* Empty Set - Set with no members
* Equal sets - Contain same members
* Subset - All members are contained in another set
* Union - Combine two sets
* Intersection - Keep members that exist in both sets
* Difference - Keep members that don't exist in both sets

### Implementation

```js
class Set {
    constructor(){
        this.dataStore = [];
    }
    add(data){
        if (this.dataStore.indexOf(data) < 0){
            this.dataStore.push(data);
            return true;
        } else {
            return false;
        }
    }
    remove(data){
        var postion = this.dataStore.indexOf(data);
        if (position > -1){
            this.dataStore.splice(position, 1);
            return true;
        } else {
            return false;
        }
    }
    size(){
        return this.dataStore.length;
    }
    contains(data){
        if (this.dataStore.indexOf(data) > -1){
            return true;
        } else {
            return false;
        }
    }
    union(set){
        var temporarySet = new Set();
        for (let i = 0; i < this.dataStore.length; ++i){
            temporarySet.add(this.dataStore[i]);
        }
        for (let i = 0; i < set.dataStore.length; ++i){
            if (!temporarySet.contains(set.dataStore[i])){
                temporarySet.dataStore.push(set.dataStore[i]);
            }
        }
        return temporarySet;
    }
    intersect(set){
        var temporarySet = new Set();
        for (let i = 0; i < this.dataStore.length; ++i){
            if (set.contains(this.dataStore[i])){
                temporarySet.add(this.dataStore[i]);
            }
        }
        return temporarySet;
    }
    subset(set){
        if (this.size() > set.size()){
            return false;
        } else {
            for each (let member in this.dataStore){
                if (!set.contains(member)){
                    return false;
                }
            }
        }
        return true;
    }
    difference(set){
        var temporarySet = new Set();
        for (let i = 0; i < this.dataStore.length; ++i){
            if (!set.contains(this.dataStore[i])){
                temporarySet.add(this.dataStore[i]);
            }
        }
        return temporarySet;
    }
    show(){
        return this.dataStore;
    }
}
```

## Trees

A non-linear data structure used to store data in a hierarchical manner.

### Components

* Nodes- Item of data
* Edges- Connect nodes
* Root Node - Top of the tree
* Parent Node - Preceding node
* Child Node - Descendant node
* Leaf Node - Node with no Children
* Path - Following edges from one node to another
* Tree traversal - Visiting all of the nodes in some order
* Level - Root node is 0, all of its children are 1, etc.
* Subtree - The tree defined by calling any node a root node
* Key value - The value of a node

## Binary Trees

A non-linear data structure used to store data in a hierarchical manner. Binary trees have no more than 2 child nodes.

### Components

* Left node / Right node - Different kinds of values get stored in each

### Used For:

* Fast to search (unlike linked list), insert, and delete (unlike array)

### Implementation

```js
class Node {
    constructor(data, left, right){
        this.data = data;
        this.left = left;
        this.right = right;
    }
    show(){
        return this.data;
    }
}
```

### Binary Search Trees

#### Components

* Left node / Right node - Lesser values in the left node, greater values in the right node
* In-Order Traversal - Visit all of the nodes in the BST in ascending order of the node key values
* Pre-Order Traversal - Visit the root node first, followed by the nodes in the sub-trees under the left child of the root node, followed by the nodes in the subtrees under the right child of the root node
* Post-Order Traversal - Visit all of the children of the left subtree up to the root, then all of the children of the right subtree up to the root

#### Implementation

```js
class Node {
    constructor(data, left, right){
        this.data = data;
        this.left = left;
        this.right = right;
    }
    show(){
        return this.data;
    }
}
```

```js
class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(data){
        var node = new Node(data, null, null);
        if (this.root == null){
            this.root = node;
        } else {
            var currentNode = this.root;
            var parentNode;
            while (true){
                parentNode = currentNode;
                if (data < current.data){
                    currentNode = currentNode.left;
                    if (currentNode == null){
                        parentNode.left = node;
                        break;
                    }
                } else {
                    currentNode = currentNode.right;
                    if (currentNode == null){
                        parentNode.right = node;
                        break;
                    }
                }
            }
        }
    }
    inOrder(node){
        if (!(node == null)){
            inOrder(node.left);
            console.log(node.show());
            inOrder(node.right);
        }
    }
    preOrder(){
        if (!(node == null)){
            console.log(node.show());
            inOrder(node.left);
            inOrder(node.right);
        }
    }
    postOrder(){
        if (!(node == null)){
            inOrder(node.left);
            inOrder(node.right);
            console.log(node.show());
        }
    }
    getMinimum(){
        // Travels down left edge
        var currentNode = this.root;
        while(!(current.left == null)){
            currentNode = current.left;
        }
        return currentNode.data;
    }
    getMaximum(){
        // Travels down right edge
        var currentNode = this.root;
        while(!(current.right == null)){
            currentNode = current.right;
        }
        return currentNode.data;
    }
    find(data){
        var currentNode = this.root;
        while (currentNode.data != data){
            if (data < currentNode.data){
                currentNode = currentNode.left;
            } else {
                currentNode = currentNode.right;
            }

            if (currentNode == null){
                return null;
            }
        }
        return current;
    }
    remove(data){
        removeNode(this.root, data);
    }
    removeNode(node, data){
        if (node == null){
            return null;
        }
        if (data == node.data){
            // node has no children
            if (node.left == null && node.right == null){
                return null
            }
            // node has no left child
            if (node.left == null) {
                return node.right;
            }
            // node has no right child
            if (node.right == null) {
                return node.left;
            }
            // node has two children
            var temporaryNode = getSmallest(node.right);
            node.data = temporaryNode.data;
            node.right = removeNode(node.right,  temporaryNode.data);
            return node;
        } else if (data < node.data){
            node.left = removeNode(node.left, data);
            return node;
        } else {
            node.right = removeNode(node.right, data);
            return node;
        }
    }
}
```

## Graphs

A network.

* Looks kind of like a tree, but using nodes to represent vertices can be inefficient
* Represent edge of graph with an "adjacency list"- have an array member for each vertex and store a list of all adjacent vertices
    * Can also use an "adjacency matrix"- 2D array that indicates whether there's a connection between two vertices

### Components

* Vertex - Connection point on a graph. Can have weight (cost).
* Edge - A pair of vertices
* Directed Graph (Digraph)- Edges are ordered
* Path - Sequences of vertices such that all verticies are connected by edges. The length of a path is the number of edges from the first vertex to the last vertex. A loop has a length of 0.
* Cycle - ?
* Strongly connected - There is a path from the first vertex to the second vertex, and vice-versa.

### Used For:

* Traffic flow
* Any kind of transportation system
* Computer networks

### Implementation

```js
class Vertex {
    constructor(label){
        this.label = label;
    }
}
```

```js
class Graph {
    constructor(vertexCount){
        this.vertexCount = vertexCount;
        this.edges = 0;
        this.adjacencyList = [];
        this.marked = [];
        for (let i = 0; i < this.vertexCount; ++i){
            this.adjacencyList[i] = [];
            this.adjacencyList[i].push("");
            this.marked[i] = false;
        }
    }
    addEdge(firstVertex, secondVertex){
        this.adjacencyList[firstVertex].push(secondVertex);
        this.adjacencyList[secondVertex].push(firstVertex);
        this.edges++;
    }
    showGraph(){
        for (let i = 0; i < this.vertexCount; ++i){
            console.log(`${i} -> `);
            for (let j; j < this.vertexCount; ++j){
                if (this.adjacencyList[i][j]){
                    console.log(`${this.adjacencyList[i][j]}`);
                }
            }
        }
    }
    depthFirstSearch(vertex){
        this.marked[vertex] = true;
        for each (let nextVertex in this.adjacencyList[vertex]){
            if (!this.marked[nextVertex]){
                this.depthFirstSearch(nextVertex);
            }
        }
    }
    breadthFirstSearch(vertex){
        var queue = [];
        this.marked[vertex] = true;
        queue.push(vertex);
        //
    }
}

```
