- An Interface extended SortedSet
- A `NavigableSet` may be accessed and traversed in either ascending or descending order.
- The `descendingSet` method returns a view of the set with the senses of all relational and directional methods inverted. 
- The performance of ascending operations and views is likely to be faster than that of descending ones.
- Should not permit insertion of null elements, if you are going to implement this interface.
- Does return null, if no data exist for operation
- sorted sets of [`Comparable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html "interface in java.lang") elements intrinsically do not permit `null`

## Methods And Description

- *ceiling* - Returns the least element in this set **greater than or equal** to the given element, or null if there is no such element.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);
System.out.println(ns.ceiling(18));
```

`Output`:
[19, 20, 21, 29]
19

- *descendingIterator()* - Returns an iterator over the elements in this set, in descending order.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
  
Iterator<Integer> integerIterator = ns.descendingIterator();  
for (Iterator<Integer> it = integerIterator; it.hasNext(); ) {  
    System.out.print(it.next()+" ");  
}
```

`Output:`
[19, 20, 21, 29]
29 21 20 19 

- *descendingSet()* - Returns a reverse order view of the elements contained in this set.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
  
NavigableSet<Integer> integers = ns.descendingSet();  
System.out.println(integers);
```

`Output:`
[19, 20, 21, 29]
[29, 21, 20, 19]

- *floor(E e)* - Returns the greatest element in this set **less than or equal to the given element** , or null if there is no such element.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.floor(27));
```

`Output:`
[19, 20, 21, 29]
21

- *headset(E toElement, boolean inclusive)* - Returns a view of the portion of this set whose elements are less than (or equal to, if `inclusive` is true) `toElement`.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.headSet(29,false));  
System.out.println(ns.headSet(29,true));
```


`Output:`
[19, 20, 21, 29]
[19, 20, 21]
[19, 20, 21, 29]

- *higher(E element)* - Returns the least element in this set strictly greater than the given element, or `null` if there is no such element.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.higher(20));
```

`Output:`
[19, 20, 21, 29]
21

- *lower(E e)* -   Returns the greatest element in this set strictly less than the given element, or `null` if there is no such element.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.lower(22));
```

`Output:`
[19, 20, 21, 29]
21

- *pollFirst()* - Retrieves and removes the first (lowest) element, or returns `null` if this set is empty.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.pollFirst());  
System.out.println(ns);
```

`Output:`
[19, 20, 21, 29]
19
[20, 21, 29]

- *pollLast()* - Retrieves and removes the last (highest) element, or returns `null` if this set is empty.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.pollLast());  
System.out.println(ns);
```

`Output:`
[19, 20, 21, 29]
29
[19, 20, 21]

- *subSet(E fromElt, boolean fromInclusinve, E toElt, boolean toInclusinve)* - Returns a view of the portion of this set whose elements range from `fromElement` to `toElement`.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.subSet(20,false,29,false));  
System.out.println(ns.subSet(20,true,29,false));  
System.out.println(ns.subSet(20,false,29,true));  
System.out.println(ns.subSet(20,true,29,true));
```

`Output:`
[19, 20, 21, 29]
[21]
[20, 21]
[21, 29]
[20, 21, 29]

- *tailSet(E fromElt, boolean inclusive)* - Returns a view of the portion of this set whose elements are greater than (or equal to, if `inclusive` is true) `fromElement`.

```java
NavigableSet<Integer> ns = new TreeSet<>(); // ascending order  
ns.add(29);  
ns.add(20);  
ns.add(21);  
ns.add(19);  
System.out.println(ns);  
System.out.println(ns.tailSet(20,false));  
System.out.println(ns.tailSet(20,true));
```

`Output:`
[19, 20, 21, 29]
[21, 29]
[20, 21, 29]