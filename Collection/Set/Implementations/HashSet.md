- Backed by a HashMap instance
- No defined iteration order of the set
- Permits `null` element
- Time Complexity - O(1) for add, remove, contains and size
- Iterating over this set requires time proportional to the sum of the HashSet instance's size (the number of elements) plus the "capacity" of the backing HashMap instance (the number of buckets). Thus, it's very important not to set the initial capacity too high (or the load factor too low) if iteration performance is important.
- **Not Synchronized**
- Use Collections.synchronizedSet() to make it thread-safe
```java
Set s = Collections.synchronizedSet(new HashSet(...));
```

- Iterator methods are *fail-fast*, throws a **ConcurrentModificationException**

## Constructors

- HashSet()
- HashSet(Collection)
- HashSet(InitialCapacity) - default load factor (0.75)
- HashSet(Initialcapacity, loadfactor)

