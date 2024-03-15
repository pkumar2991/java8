- java.util.Map <K,V>
- Provides three collection views
	- Set of keys
	- Collection of values
	- Set of key-value mapping
- Order of elements depends on the implementation classes
- Key should be an immutable object
- The "destructive" methods contained in this interface, that is, ==the methods that modify the map on which they operate==, are specified to throw UnsupportedOperationException if this map does not support the operation.

## Sub Interfaces
- SortedMap
- NavigableMap
- ConcurrentMap
- ConcurrentNavigableMap

### Important Methods introduced in Java 8
- *computeIfAbsent* - If the value associated with the key is not present in the map, the output of the evaluated function would be recorded. If the function returns null no mapping is recorded.
```java
SortedMap<Integer, String> map = new TreeMap<>();  
map.put(10,"India");  
map.put(20,"London");  
map.put(30,"Canada");  
map.put(40,"Switzerland");  
map.put(50,"Vietnam");  
map.put(05,"Nepal");  
  
  
  
map.computeIfAbsent(15,(key)-> "Netherland");  
  
  
System.out.println("Map: " + map);
```

`Output:` Netherland is added as it was absent.    
Map: {5=Nepal, 10=India, **15=Netherland**, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}  
- *computeIfPresent* - If the key is present, the BiFunction is used to remap the value against the key.
```java
map.computeIfPresent(30,(key, value) -> value.toUpperCase());
```

`Output:` Map: {5=Nepal, 10=India, 20=London, 30=CANADA, 40=Switzerland, 50=Vietnam}  
Canada is converted to Upper Case Canada - CANADA.  
- *getOrDefault* - Returns the value associated with the key, otherwise returns the default value defined.
```java
String value = map.getOrDefault(99, "No Country");  
System.out.println("Map: " + map);  
System.out.println(value);
```

`Output:`  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam}
**No Country**  
- *putIfAbsent* - If the specified key is not already associated with a value (or is mapped to null) associates it with the given value and returns null, else returns the current value
```java
String value = map.putIfAbsent(99, "Germany");  
System.out.println("Map: " + map);  
System.out.println(value);
```

`Output:` Added Germany as it was not present in the map and returns null as previous value.  
Map: {5=Nepal, 10=India, 20=London, 30=Canada, 40=Switzerland, 50=Vietnam, 99=Germany}
null