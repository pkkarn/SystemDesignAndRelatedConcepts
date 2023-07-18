# Linked List

## Singly Linked List:

It grows dynamically(as opposed to an array where length is sort of fixed), and each item is linked
to the their next item in the list(because of this it takes more memory to store that).

In terms, of data elements there would be 3 things:

```js
{ // starts with head
    Value,
    NextItemPointer ->
} {
    Value,
    NextItemPointer -> 
} NULL // ends at null
```

**Big O Notation**:

- Access: O(n) (N iteration to find element at nth place)
- Insert at head: O(1) (just assign next of linked list to head)
- Insert at end: O(n) (you have to reach last before you do so)

**Useful**

- When you want to access things sequentially
- Good for stacks(LIFO) or queue(FIFO)
- One pointer per node = lower memory requirements


## Doubly Linked List:

Concept is more or less same but here each item points to two items, next and previous item. And because now we are storing two pointers that's why you are using more memory

And here you will have

```
NULL
{ // starts with head
    PrevItemPointer <-
    Value,
    NextItemPointer ->
} {
    PrevItemPointer <-
    Value,
    NextItemPointer ->
} {
    PrevItemPointer <-
    Value,
    NextItemPointer -> 
} NULL // ends at null
```

Here you can track head and tail pointers, although you can also track tail single linked list but it doesn't make that much sense as you can't go back there

**Big O Notation**:

- Access: O(n) (N/2 = N) [Because you can either start from end or head]
- Insert at head and tail: O(1) (just assign next of linked list to head)

**Useful**

- Deques
- MRU(Most Recently Used)

