- An Interface extended SortedSet
- A `NavigableSet` may be accessed and traversed in either ascending or descending order.
- The `descendingSet` method returns a view of the set with the senses of all relational and directional methods inverted. 
- The performance of ascending operations and views is likely to be faster than that of descending ones.
- Should not permit insertion of null elements, if you are going to implement this interface.
- Does return null, if no data exist for operation
- sorted sets of [`Comparable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html "interface in java.lang") elements intrinsically do not permit `null`

## Methods And Description

- *ceiling* - Returns the last element in this set **greater than or equal** to the given element, or null if there is no such element.

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
