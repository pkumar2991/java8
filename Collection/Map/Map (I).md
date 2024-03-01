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
