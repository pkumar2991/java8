- TreeSet is a NavigableSet implementation backed by TreeMap instance.
- Followed by natural ordering or by a comparator provided at set creation time
- Time complexity - Guaranteed log(n) for add, remove and contains
- Irrespective of comparator- ordering is ***consistent* with *equals***
- The ordering imposed by a comparator c on a set of elements S is said to be _consistent with equals_ if and only if *c.compare(e1, e2) == 0* has the same boolean value as *e1.equals(e2)* for every e1 and e2 in S.
- **Not synchronised** - Not thread safe
- Use *Collections.synchronizedSortedSet()*
- The iterators returned by this class's `iterator` method are _fail-fast_: if the set is modified at any time after the iterator is created, in any way except through the iterator's own `remove` method, the iterator will throw a [`ConcurrentModificationException`](https://docs.oracle.com/javase/8/docs/api/java/util/ConcurrentModificationException.html "class in java.util").


Constructors internally creates TreeMap Object

```java
public TreeSet() {  
    this(new TreeMap<>());  
}
public TreeSet(Comparator<? super E> comparator) {  
    this(new TreeMap<>(comparator));  
}
public TreeSet(Collection<? extends E> c) {  
    this();  
    addAll(c);  
}
public TreeSet(SortedSet<E> s) {  
    this(s.comparator());  
    addAll(s);  
}
```

## How add works in TreeSet

```java

// Dummy value to associate with an Object in the backing Map  
private static final Object PRESENT = new Object();
public boolean add(E e) {  
    return m.put(e, PRESENT)==null;  
}
```

`Adds the specified element to this set if it is not already present. More formally, adds the specified element e to this set if the set contains no element e2 such that Objects.equals(e, e2). If this set already contains the element, the call leaves the set unchanged and returns false.`

`Params:`
e – element to be added to this set
Returns:
	true if this set did not already contain the specified element
Throws:
	ClassCastException – if the specified object cannot be compared with the elements currently in this set
	NullPointerException – if the specified element is null and this set uses natural ordering, or its comparator does not permit null elements

## How to remove in TreeSet

```java
public boolean remove(Object o) {  
    return m.remove(o)==PRESENT;  
}
```

## Time Complexity
O(log n) - For add, remove and contains

## Clone in TreeSet

Shallow copy

```java
public Object clone() {  
    TreeSet<E> clone;  
    try {  
        clone = (TreeSet<E>) super.clone();  
    } catch (CloneNotSupportedException e) {  
        throw new InternalError(e);  
    }  
  
    clone.m = new TreeMap<>(m);  
    return clone;  
}
```

## Not allow to store null value

```java
TreeSet<Integer> treeSet = new TreeSet<>();  
treeSet.add(null);
```

`Exception:`
```java
Exception in thread "main" java.lang.NullPointerException: Cannot invoke "java.lang.Comparable.compareTo(Object)" because "k1" is null
	at java.base/java.util.TreeMap.compare(TreeMap.java:1569)
	at java.base/java.util.TreeMap.addEntryToEmptyMap(TreeMap.java:776)
	at java.base/java.util.TreeMap.put(TreeMap.java:785)
	at java.base/java.util.TreeMap.put(TreeMap.java:534)
	at java.base/java.util.TreeSet.add(TreeSet.java:255)
```

