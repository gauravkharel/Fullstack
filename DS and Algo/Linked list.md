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


