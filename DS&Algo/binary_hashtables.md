# Binary Tree

- Each node will have either left and right children
- if left and right ordered, e.g left is always less and right is always greater, then its Binary Search Tree
- Access is O(log(n)) because we are almost slicing half of the nodes in one search...e.g we have to 
search around 18 nodes then, and in worst case scenario O(n)... if its one sided

- Inserts and deletes also O(log(n)) in the best case and O(n) worst case... Because you are not re-arranging elements

- Mostly used in cases where you need to do in-order traversals

# Hash Tables:

In hash tables you generate hash functions quickly maps some key to bucket and then that bucket can
hold one more than one value for those keys that are mapped for that particular bucket... Although
you have to make sure that you don't put lot items in one bucket.

`Question`: Is my defintion true?

Yes, your definition of hash tables is generally correct, but I'll clarify some points and provide a slightly more detailed explanation.

A hash table is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash function is used to compute an index into an array of buckets or slots, from which the desired value can be found.

Here's a more comprehensive explanation:

In a hash table, you use a hash function to map keys to buckets. The purpose of the hash function is to distribute the keys evenly across the buckets. Each bucket can hold one or more values. This is because different keys might hash to the same bucket, leading to what is known as a hash collision.

When a hash collision occurs, there are several ways to handle it. One common method is chaining, where each bucket contains a list of elements that hash to the same bucket. Another method is open addressing, where if a bucket is already occupied, the hash table seeks to place the value in the next available slot.

It's important to prevent buckets from becoming too full to maintain efficient performance. As you've mentioned, you don't want to put too many items in one bucket. If the load factor (the number of entries divided by the number of buckets) gets too high, the hash table can be resized, typically by doubling the number of buckets.

So, in summary, a hash table is a data structure that uses a hash function to map keys to buckets, and each bucket can hold one or more values corresponding to keys that hash to the same bucket. Proper management of the hash table is necessary to maintain performance.

### For a well-implemented hash table:

- Access: The average time complexity for accessing an item is O(1), which is constant time complexity. This is because once you've computed the hash and resolved any collisions, you should be able to access any element directly.

- Deletion: Similarly, deletion in a hash table also has an average time complexity of O(1) for the same reasons.

However, these are average cases. In the worst-case scenario (such as when all keys hash to the same bucket), access and deletion could become O(n), where n is the number of keys. To mitigate this, a good hash function is needed to ensure that the keys are well-distributed, and the load factor of the table should be well-managed. 

Also, it's worth mentioning that these time complexities assume a perfect hash function that assigns each key to a unique bucket. But in reality, because of hash collisions, this isn't always the case, and the time complexity for these operations may degrade to O(n) in a poorly constructed hash table or with a bad hash function.

Keep in mind these are theoretical values. Actual performance of a hash table can vary widely and depends on many factors including the quality of the hash function, the load factor, how hash collisions are handled, etc.