- CopyOnWriteArrayList is a concurrent alternative of synchronized List. CopyOnWriteArrayList provides better concurrency than synchronized List by allowing multiple concurrent reader and replacing the whole list on write operation.
- write operation is costly on CopyOnWriteArrayList but it performs better when there are multiple reader and requirement of iteration is more than writing

A [`Set`](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html "interface in java.util") that uses an internal [`CopyOnWriteArrayList`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CopyOnWriteArrayList.html "class in java.util.concurrent") for all of its operations. Thus, it shares the same basic properties:

- It is best suited for applications in which set sizes generally stay small, read-only operations vastly outnumber mutative operations, and you need to prevent interference among threads during traversal.
- It is thread-safe.
- Mutative operations (`add`, `set`, `remove`, etc.) are expensive since they usually entail copying the entire underlying array.
- Iterators do not support the mutative `remove` operation.
- Traversal via iterators is fast and cannot encounter interference from other threads. Iterators rely on unchanging snapshots of the array at the time the iterators were constructed.

## Constructors
- CopyOnWriteArraySet()
- CopyOnWriteArraySet(Collection` <? extends E>`  c)
