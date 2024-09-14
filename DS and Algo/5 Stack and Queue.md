	[[Drawing 2024-09-10 08.38.49.excalidraw]]
#### **1. Stack Overview:**
A **stack** is a LIFO (Last In, First Out) data structure. The element inserted last is the first to be removed. Think of it like stacking books: the last book placed on top is the first one you take off.

- **Key Operations**:
  - **Push**: Add an element to the top of the stack.
  - **Pop**: Remove and return the top element.
  - **Peek/Top**: View the top element without removing it.
  - **isEmpty**: Check if the stack is empty.

- **Time Complexity**:
  - **Push/Pop/Peek/IsEmpty**: `O(1)` for all operations since they only deal with the top element.

- **TypeScript Example**:
```typescript
class Stack<T> {
    private items: T[] = [];

    push(item: T): void {
        this.items.push(item);
    }

    pop(): T | undefined {
        return this.items.pop();
    }

    peek(): T | undefined {
        return this.items[this.items.length - 1];
    }

    isEmpty(): boolean {
        return this.items.length === 0;
    }
}
```

#### **2. Queue Overview:**
A **queue** is a FIFO (First In, First Out) data structure. The element inserted first is the first one to be removed. Think of it like standing in line: the first person in line is served first.

- **Key Operations**:
  - **Enqueue**: Add an element to the end (rear) of the queue.
  - **Dequeue**: Remove and return the front element.
  - **Peek/Front**: View the front element without removing it.
  - **isEmpty**: Check if the queue is empty.

- **Time Complexity**:
  - **Enqueue/Dequeue/Peek/IsEmpty**: `O(1)` for all operations with an optimized implementation using a linked list.

- **TypeScript Example**:
```typescript
class Queue<T> {
    private items: T[] = [];

    enqueue(item: T): void {
        this.items.push(item);
    }

    dequeue(): T | undefined {
        return this.items.shift();
    }

    front(): T | undefined {
        return this.items[0];
    }

    isEmpty(): boolean {
        return this.items.length === 0;
    }
}
```

#### **3. Differences Between Stack and Queue**:
- **Order**:
  - Stack: LIFO (last in, first out).
  - Queue: FIFO (first in, first out).
  
- **Usage**:
  - **Stack**: Used in function calls, undo/redo functionality, depth-first search (DFS).
  - **Queue**: Used in scheduling, breadth-first search (BFS), and resource sharing.

#### **4. Implementations**:
Stacks and queues can be implemented using arrays or linked lists:
- **Array-based** implementations are straightforward for both stack and queue but can lead to resizing issues (in dynamic arrays).
- **Linked List-based** implementations are more flexible but require handling pointers.

#### **5. Common Problems**:
- **Stack Problems**: Balanced Parentheses, Next Greater Element, Min Stack.
- **Queue Problems**: Implementing a queue with two stacks, Rotting Oranges (BFS), Circular Queue.

