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

### Used For:

* Every situation where a 1-dimensional array works, except not when you need random access to elements
* Insertion and deletion are really efficient

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

## Dictionaries

## Hashing

## Sets

## Binary Trees

## Binary Search Trees

## Graphs
