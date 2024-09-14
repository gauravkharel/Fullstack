```
interface ILinkedList<T> {
  insertInBegin(data: T): Node<T>;
  insertAtEnd(data: T): Node<T>;
  deleteNode(node: Node<T>): void;
  traverse(): T[];
  size(): number;
  search(comparator: (data: T) => boolean): Node<T> | null;
}
```


Every linked list is technically a tree. 

```
// we implemented doubly linked list so, here it is. 
as a example

1<-->2<-->3
prepend(1) 
=> // Adds to the front ->  1<->1<->2<->3

append(2)
=> // Adds to the last -> 1<->1<->2<->3<->2

insertAt(12, 1)
=> 1<->12<->1<->2<->3<->2

remove(2)// the first value that is 2
=> 1<->12<->1<->3<->2

get(1) => get index at 1
=> 12

removeAt(2)
=> 1<->12<->3<->2
```

here's the code implementation
```
type Node<T> = {
    value: T,
    prev?: Node<T>,
    next?: Node<T>
}

export default class DoublyLinkedList<T> {
    public length: number;
    private head?: Node<T>
    private tail?: Node<T>

    constructor() {
        this.length = 0;
        this.head = undefined;
        this.tail = undefined;
    }

    private debug() {
        let curr = this.head;
        let out = "";
        for (let i = 0; curr && i < this.length; ++i) {
            out += `${i} => ${curr.value} `;
            curr = curr.next;
        }
        console.log(out);
    }

    prepend(item: T): void {
        const node = { value: item } as Node<T>;
        this.length++;

        if (!this.head) {
            this.head = this.tail = node;
            return;
        }

        node.next = this.head;
        this.head.prev = node;
        this.head = node;
    }

    append(item: T): void {
        const node = { value: item } as Node<T>;
        this.length++;

        if (!this.tail) {
            this.head = this.tail = node;
            return;
        }

        node.prev = this.tail;
        this.tail.next = node;
        this.tail = node;
    }

    insertAt(item: T, idx: number): void {
        if (idx > this.length || idx < 0) {
            throw new Error("Index out of bounds");
        }

        if (idx === 0) {
            this.prepend(item);
            return;
        }

        if (idx === this.length) {
            this.append(item);
            return;
        }

        this.length++;
        let curr = this.getAt(idx) as Node<T>;

        const node = { value: item } as Node<T>;
        node.next = curr;
        node.prev = curr.prev;

        if (curr.prev) {
            curr.prev.next = node;
        }
        curr.prev = node;

        if (idx === 0) {
            this.head = node;
        }
    }

    remove(item: T): T | undefined {
        let curr = this.head;
        for (let i = 0; curr && i < this.length; i++) {
            if (curr.value === item) {
                return this.removeNode(curr);
            }
            curr = curr.next;
        }
        return undefined;
    }

    get(idx: number): T | undefined {
        const node = this.getAt(idx);
        return node?.value;
    }

    removeAt(idx: number): T | undefined {
        const node = this.getAt(idx);
        if (!node) {
            return undefined;
        }
        return this.removeNode(node);
    }

    private removeNode(node: Node<T>): T | undefined {
        this.length--;

        if (node.prev) {
            node.prev.next = node.next;
        }
        if (node.next) {
            node.next.prev = node.prev;
        }

        if (node === this.head) {
            this.head = node.next;
        }
        
        if (node === this.tail) {
            this.tail = node.prev;
        }
        
        node.prev = node.next = undefined;
        return node.value;
    }

    private getAt(idx: number): Node<T> | undefined {
        if (idx < 0 || idx >= this.length) {
            return undefined;
        }

        let curr = this.head;
        for (let i = 0; curr && i < idx; ++i) {
            curr = curr.next;
        }
        return curr;
    }
}

```


### 1. **What is a Linked List?**
A **Linked List** is a linear data structure where each element (node) points to the next one, allowing for efficient insertions and deletions. Unlike arrays, linked lists do not store elements contiguously in memory.

#### Key Concepts:
- **Node**: The basic unit of a linked list, consisting of:
  - A **value** (or data).
  - A **pointer/reference** to the next node (and possibly a previous node in a doubly linked list).
  
- **Head**: The first node in the linked list.
- **Tail**: The last node (for a doubly linked list, this is useful when you need to traverse the list from the end).

### 2. **Singly Linked List in TypeScript**

#### Structure of a Node:
In a **singly linked list**, each node contains:
- A **value**: The data the node holds.
- A **next** pointer: A reference to the next node in the list.

#### TypeScript Implementation:

```typescript
class ListNode {
    value: number; // The value/data stored in the node
    next: ListNode | null; // Reference to the next node

    constructor(value: number, next: ListNode | null = null) {
        this.value = value;
        this.next = next;
    }
}
```

In this class:
- `value`: Stores the node's value.
- `next`: Points to the next node (or `null` if it's the last node).

#### Singly Linked List Class:

```typescript
class SinglyLinkedList {
    head: ListNode | null;

    constructor() {
        this.head = null;
    }

    // Insert at the beginning of the list
    insertAtHead(value: number): void {
        const newNode = new ListNode(value);
        newNode.next = this.head;
        this.head = newNode;
    }

    // Insert at the end of the list
    insertAtTail(value: number): void {
        const newNode = new ListNode(value);
        if (!this.head) {
            this.head = newNode;
            return;
        }
        let current = this.head;
        while (current.next !== null) {
            current = current.next;
        }
        current.next = newNode;
    }

    // Delete the first occurrence of a value
    delete(value: number): void {
        if (!this.head) return;

        if (this.head.value === value) {
            this.head = this.head.next;
            return;
        }

        let current = this.head;
        while (current.next && current.next.value !== value) {
            current = current.next;
        }

        if (current.next) {
            current.next = current.next.next;
        }
    }

    // Print the list
    printList(): void {
        let current = this.head;
        while (current) {
            console.log(current.value);
            current = current.next;
        }
    }
}
```

### Key Operations:
1. **Insertion**:
   - `insertAtHead()`: Adds a new node at the start.
   - `insertAtTail()`: Adds a new node at the end.
   
2. **Deletion**:
   - Deletes a node with a specific value.
   
3. **Traversal**:
   - `printList()`: Prints all values in the list, moving from the head to the tail.

### 3. **Doubly Linked List in TypeScript**

In a **doubly linked list**, each node points to both the **next** and the **previous** node.

#### Structure of a Node:

```typescript
class DoublyListNode {
    value: number;
    next: DoublyListNode | null;
    prev: DoublyListNode | null;

    constructor(value: number, next: DoublyListNode | null = null, prev: DoublyListNode | null = null) {
        this.value = value;
        this.next = next;
        this.prev = prev;
    }
}
```

Here, `prev` is a reference to the previous node.

#### Doubly Linked List Class:

```typescript
class DoublyLinkedList {
    head: DoublyListNode | null;
    tail: DoublyListNode | null;

    constructor() {
        this.head = null;
        this.tail = null;
    }

    // Insert at the head of the list
    insertAtHead(value: number): void {
        const newNode = new DoublyListNode(value);
        if (!this.head) {
            this.head = newNode;
            this.tail = newNode;
        } else {
            newNode.next = this.head;
            this.head.prev = newNode;
            this.head = newNode;
        }
    }

    // Insert at the tail of the list
    insertAtTail(value: number): void {
        const newNode = new DoublyListNode(value);
        if (!this.tail) {
            this.head = newNode;
            this.tail = newNode;
        } else {
            newNode.prev = this.tail;
            this.tail.next = newNode;
            this.tail = newNode;
        }
    }

    // Delete a node with a specific value
    delete(value: number): void {
        if (!this.head) return;

        let current = this.head;
        while (current && current.value !== value) {
            current = current.next;
        }

        if (current) {
            if (current.prev) {
                current.prev.next = current.next;
            } else {
                this.head = current.next; // Update head if we're removing the first node
            }

            if (current.next) {
                current.next.prev = current.prev;
            } else {
                this.tail = current.prev; // Update tail if we're removing the last node
            }
        }
    }

    // Print the list from head to tail
    printList(): void {
        let current = this.head;
        while (current) {
            console.log(current.value);
            current = current.next;
        }
    }

    // Print the list from tail to head
    printReverse(): void {
        let current = this.tail;
        while (current) {
            console.log(current.value);
            current = current.prev;
        }
    }
}
```

### Key Operations:
1. **Insertion**:
   - `insertAtHead()`: Adds a new node at the start.
   - `insertAtTail()`: Adds a new node at the end.
   
2. **Deletion**:
   - Deletes a node with a specific value.
   
3. **Traversal**:
   - `printList()`: Prints all values from the head to the tail.
   - `printReverse()`: Prints values from the tail to the head (this is unique to doubly linked lists).

### 4. **Comparison: Singly vs. Doubly Linked Lists**

| Feature               | Singly Linked List                      | Doubly Linked List                            |
|-----------------------|-----------------------------------------|----------------------------------------------|
| **Memory Usage**       | Less (one pointer per node)             | More (two pointers per node: next and prev)  |
| **Traversal**          | Only forward                           | Forward and backward                         |
| **Insertion/Deletion** | Efficient at head, but not at the tail  | Efficient at both head and tail              |
| **Use Cases**          | Lightweight, simple lists               | When bidirectional traversal is necessary    |

### 5. **Linked List Use Cases**:
- **Singly Linked List**:
  - Simple use cases where one-way traversal is sufficient (e.g., a queue).
  
- **Doubly Linked List**:
  - More complex scenarios where you need to traverse back and forth (e.g., implementing a browser history, or a playlist).

### Summary:
1. **Singly Linked List**: Simple structure, less memory, only forward traversal.
2. **Doubly Linked List**: More complex, supports backward traversal and easier to manipulate from both ends.

.
