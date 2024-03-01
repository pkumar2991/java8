A scalable concurrent [`NavigableSet`](https://docs.oracle.com/javase/8/docs/api/java/util/NavigableSet.html "interface in java.util") implementation based on a [`ConcurrentSkipListMap`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/ConcurrentSkipListMap.html "class in java.util.concurrent"). The elements of the set are kept sorted according to their [natural ordering](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html "interface in java.lang"), or by a [`Comparator`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html "interface in java.util") provided at set creation time, depending on which constructor is used.

This implementation provides expected average _log(n)_ time cost for the `contains`, `add`, and `remove` operations and their variants. Insertion, removal, and access operations safely execute concurrently by multiple threads.

Iterators and spliterators are [_weakly consistent_](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/package-summary.html#Weakly).

`Ascending ordered views and their iterators are faster than descending ones.`

==Beware that, unlike in most collections, the `size` method is _not_ a constant-time operation. Because of the asynchronous nature of these sets, determining the current number of elements requires a traversal of the elements, and so may report inaccurate results if this collection is modified during traversal. Additionally, the bulk operations `addAll`, `removeAll`, `retainAll`, `containsAll`, `equals`, and `toArray` are _not_ guaranteed to be performed atomically. For example, an iterator operating concurrently with an `addAll` operation might view only some of the added elements.==

This class and its iterators implement all of the _optional_ methods of the [`Set`](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html "interface in java.util") and [`Iterator`](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html "interface in java.util") interfaces. Like most other concurrent collection implementations, this class does not permit the use of `null` elements, because `null` arguments and return values cannot be reliably distinguished from the absence of elements.

