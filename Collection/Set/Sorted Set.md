- An Interface
- Maintains Natural order or follow comparator passed through constructor
- Element must implement the comparable interface
- Exception - *ClassCastException* - if elements are not mutually comparable

`SortedSet<String> sub = s.subSet(low, high+"\0")` - closed range
`SortedSet<String> sub = s.subSet(low+"\0", high)` - open range

## Methods And Description
- *comparator()* - Returns the comparator used to order the elements in this set, or null if this set uses the [natural ordering](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html "interface in java.lang") of its elements.
- *first()* - Returns the first element currently in the set.
  
```java
SortedSet<Integer> ss = new TreeSet<>(Comparator.reverseOrder());  
ss.add(29);  
ss.add(20);  
ss.add(21);  
ss.add(19);  
System.out.println(ss);  
System.out.println(ss.first());
```

`output:`  
[29, 21, 20, 19]  
29

- *headSet(E toElement)* - Returns a view of the portion of this set whose elements are strictly less than toElement (Follow Natural ordering)

```java
SortedSet<Integer> ss = new TreeSet<>();  
ss.add(29);  
ss.add(20);  
ss.add(21);  
ss.add(19);  
System.out.println(ss);  
System.out.println(ss.headSet(21));
```

`Output:`  
[19, 20, 21, 29]  
[19, 20]


- *last()* - Returns the last highest element currently in the set.

```java
SortedSet<Integer> ss = new TreeSet<>();  
ss.add(29);  
ss.add(20);  
ss.add(21);  
ss.add(19);  
System.out.println(ss);  
System.out.println(ss.last());
```

`Output:`  
[19, 20, 21, 29]  
[29]

- *subSet* - Returns a view of the portion of this set whose elements range from fromElement, inclusive, toElement, exclusive.

```java
SortedSet<Integer> ss = new TreeSet<>();  
ss.add(29);  
ss.add(20);  
ss.add(21);  
ss.add(19);  
System.out.println(ss);  
SortedSet<Integer> subset = ss.subSet(20, 29);  
System.out.println(subset);
```

`Output`:  
[19, 20, 21, 29]  
[20, 21]

- *tailSet(E fromElement)* - Returns a view of the portion of this set whose elements are greater than or equal to fromElement.

```java
SortedSet<Integer> ss = new TreeSet<>();  
ss.add(29);  
ss.add(20);  
ss.add(21);  
ss.add(19);  
System.out.println(ss);  
System.out.println(ss.tailSet(20));
```

`Output:`  
[19, 20, 21, 29]  
[20, 21, 29]