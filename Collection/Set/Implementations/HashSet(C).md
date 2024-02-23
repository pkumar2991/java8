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
- HashSet(Initialcapacity, loadfactor) - it creates an Instance of LinkedHashMap

## Internal working
Hashset uses HashMap internally, hashset elements are stored as keys of the map and value for these keys are constant.

### Add an element

`Adds the specified element to this set if it is not already present. More formally, adds the specified element e to this set if this set contains no element e2 such that Objects.equals(e, e2). If this set already contains the element, the call leaves the set unchanged and returns false.`
`Params:`
`e – element to be added to this set`
`Returns:`
`true if this set did not already contain the specified element`

```java
public boolean add(E e) {  
    return map.put(e, PRESENT)==null;  
}
```

### Remove an element

`Removes the specified element from this set if it is present. More formally, removes an element e such that Objects.equals(o, e), if this set contains such an element. Returns true if this set contained the element (or equivalently, if this set changed as a result of the call). (This set will not contain the element once the call returns.)`
`Params:`
`o – object to be removed from this set, if present`
`Returns:`
`true if the set contained the specified element`  

```java
public boolean remove(Object o) {  
    return map.remove(o)==PRESENT;  
}
```

