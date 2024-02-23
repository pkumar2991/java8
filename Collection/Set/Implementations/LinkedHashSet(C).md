- Extends Hashset and implemented Set, Cloneable, Serializable
- Backed by LinkedHashMap
- Maintains a doubly-linked list
- Maintains the `insertion-order`
- Duplicate element not allowed
- Permits `null` elements
- provides constant-time performance for the basic operations (add, contains and remove), assuming the hash function disperses elements properly among the buckets.
- Performance is likely to be just slightly below that of HashSet, due to the added expense of maintaining the linked list, with one exception: Iteration over a LinkedHashSet requires time proportional to the _size_ of the set, regardless of its capacity.
- Iteration over a **HashSet** is likely to be more expensive, requiring time proportional to its _capacity_.
- Not synchronized. 
```java
Set s = Collections.synchronizedSet(new LinkedHashSet(...));
```
- The iterators returned by this class's iterator method are _fail-fast_: if the set is modified at any time after the iterator is created, in any way except through the iterator's own remove method, the iterator will throw a [`ConcurrentModificationException`](https://docs.oracle.com/javase/8/docs/api/java/util/ConcurrentModificationException.html "class in java.util").

## Constructors
- LinkedHashSet()
- LinkedHashSet(`Collection<? extends E> c`)
- LinkedHashSet(int initialCapacity)
- LinkedHashSet(int initialCapacity, float loadFactor)

## Internal Working

Any constructor of LinkedHashSet internally call the constructor of super class i.e.. HashSet. 

```java
public LinkedHashSet(int initialCapacity, float loadFactor) {  
    super(initialCapacity, loadFactor, true);  
}
```

`Super Constructor from` **HashSet** - `creates an instance of LinkedHashMap
`Constructs a new, empty linked hash set. (This package private constructor is only used by LinkedHashSet.) The backing HashMap instance is a LinkedHashMap with the specified initial capacity and the specified load factor.`
`Params:`
`initialCapacity – the initial capacity of the hash map loadFactor – the load factor of the hash map dummy – ignored (distinguishes this constructor from other int, float constructor.)`
`Throws:`
`IllegalArgumentException – if the initial capacity is less than zero, or if the load factor is nonpositive`

```java
HashSet(int initialCapacity, float loadFactor, boolean dummy) {  
    map = new LinkedHashMap<>(initialCapacity, loadFactor);  
}
```

Add / remove - operation works as per LinkedHashMap having a constant value for all keys.