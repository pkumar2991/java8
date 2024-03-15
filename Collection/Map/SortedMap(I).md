- Provides ordering on its keys
- Followed natural ordering or by a Comparator
- Keys must implement Comparable Interface or specified comparator
- This interface is the map analogue of SortedSet

## Methods
*comparator()* - Returns the comparator used to order the keys in this map, or null if this map uses the natural ordering of its keys

```java
SortedMap<String,Integer> map = new TreeMap<>((a, b)-> b.length() - a.length());  
System.out.println(map.comparator());
```

`Output`: `collections.map.MySortedMap$$Lambda$14/0x00000008010031f0@28a418fc`

*entryset()* - Returns Set<Map.Entry<K,V>>

```java
SortedMap<String, Integer> map = new TreeMap<>(Comparator.reverseOrder());  
map.put("A", 10);  
map.put("B", 30);  
map.put("C", 20);  
  
map.entrySet().forEach(e -> {  
    System.out.println(e.getKey() + "-" + e.getValue());  
});
```

`Output:` 
C-20  
B-30  
A-10  

*firstKey()* - Returns the first (lowest) key currently in this map
```java
System.out.println(map.firstKey());
```

`Output:` C  

*headMap(K toKey)* - Returns a view of the portion of this map whose keys are strictly less than toKey. The returned map is backed by this map, so changes in the returned map are reflected in this map, and vice-versa.

```java
SortedMap<Integer, String> map = new TreeMap<>();  
map.put(10,"India");  
map.put(20,"London");  
map.put(30,"Canada");  
map.put(40,"Switzerland");  
map.put(50,"Vietnam");  
map.put(05,"Nepal");  
  
System.out.println("Map: " + map);  
System.out.println("HeadMap: " + map.headMap(30));
```

`Output:`   
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
HeadMap: {5=Nepal, 10=India, 20=London}  

*keySet()* - Returns a Set view of the keys contained in this map. The set's iterator returns the keys in ascending order. The set is backed by the map, so changes to the map are reflected in the set, and vice-versa. 

```java
System.out.println("Map: " + map);  
System.out.println("KeySet: " + map.keySet());
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
KeySet: [5, 10, 20, 30, 40, 50]  

*lastKey()* - Returns the last (highest) key currently in this map

```java
System.out.println("Map: " + map);  
System.out.println("LastKey: " + map.lastKey());
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
LastKey: 50  

*subMap(K fromKey, K toKey)* - Returns a view of the portion of this map whose keys range from fromKey, inclusive, to toKey, exclusive. (If fromKey and toKey are equal, the returned map is empty.) The returned map is backed by this map, so changes in the returned map are reflected in this map, and vice-versa. The returned map supports all optional map operations that this map supports.
The returned map will throw an IllegalArgumentException on an attempt to insert a key outside its range.

```java
System.out.println("Map: " + map);  
System.out.println("SubMap: " + map.subMap(20,40));
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}
SubMap: {20=London, 30=Canada}

*tailMap(K fromKey)* - Returns a view of the portion of this map whose keys are greater than or equal to fromKey. The returned map is backed by this map, so changes in the returned map are reflected in this map, and vice-versa. The returned map supports all optional map operations that this map supports.
The returned map will throw an IllegalArgumentException on an attempt to insert a key outside its range.

```java
System.out.println("Map: " + map);  
System.out.println("TailMap: " + map.tailMap(40));
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
TailMap: {40=Switzerland, 50=Vietnam}  

*values()* - Returns a Collection view of the values contained in this map. The collection's iterator returns the values in ascending order of the corresponding keys. The collection is backed by the map, so changes to the map are reflected in the collection, and vice-versa. If the map is modified while an iteration over the collection is in progress (except through the iterator's own remove operation), the results of the iteration are undefined. The collection supports element removal, which removes the corresponding mapping from the map, via the Iterator.remove, Collection.remove, removeAll, retainAll and clear operations. **It does not support the add or addAll operations.**

```java
System.out.println("Map: " + map);  
System.out.println("Values: " + map.values());
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
Values: [Nepal, India, London, Canada, Switzerland, Vietnam]  