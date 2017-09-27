# Introduction
Stack is a LIFO (Last in first out) data structure.

# Operations

1. **pop()** – adds an element in the stack.
2. **push()** – removes an element from the stack.
3. **peek()** – get the top element without removing it.
4. **isEmpty()** – checks whether stack is empty or not.
5. **isFull()** – checks whether stack is full or not.

# Implementation

There are 2 ways to implement a stack.

1. **Array-based Stack**
2. **Linked List based Stack**

# Array-based Stack

```java runnable
public class Stack {

    private int top;
    private int capacity;
    private int[] array;

    public Stack(int capacity){
        this.capacity = capacity;
        this.array = new int[capacity];
        this.top = -1;
    }

    public boolean isFull(){
        return this.top == this.capacity - 1;
    }

    public boolean isEmpty(){
        return this.top == -1;
    }

    public void push(int value){
        if (this.isFull()) {
            return;
        }
        this.array[++this.top] = value;
        System.out.println(String.format("%d pushed.", value));
    }

    public int pop(){
        if (this.isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return this.array[this.top--];
    }

    public int peek(){
        if (this.isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return this.array[this.top];
    }

    public static void main(String[] args) {
        //capacity
        Stack stack = new Stack(5);
        stack.push(1);
        stack.push(2);
        stack.push(3);

        System.out.println(String.format("%d popped", stack.pop()));
        System.out.println(String.format("%d peeked", stack.peek()));

    }
}
```

**Pros:-**
+ Easier to use.
+ Less memory allocation because no need to track the next node.

**Cons:-**
+ Fixed size – can not increase or decrease the array.

# Link List based Stack

```java runnable
class StackNode {
    int data;
    StackNode next;
}
public class Stack {

    private StackNode root;

    public boolean isEmpty(){
        return this.root == null;
    }

    public void push(int data){
        StackNode stackNode = new StackNode();
        stackNode.data = data;
        stackNode.next = root;

        this.root = stackNode;
        System.out.println(String.format("%d pushed.", data));
    }

    public int pop(){
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }

        StackNode tempNode = this.root;
        this.root = tempNode.next;

        return tempNode.data;
    }

    public int peek(){
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }

        return this.root.data;
    }

    public static void main(String[] args) {
        Stack stack = new Stack();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(String.format("%d popped.", stack.pop()));
        System.out.println(String.format("%d peeked.", stack.peek()));
    }
}
```

**Pros:-**
+ Easily increase or decrease the Stack size.

**Cons:-**
+ Requires extra memory to keep details about next node.
