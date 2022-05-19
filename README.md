# eo-collections
Objectionary collections for EO language

This repository is for the [objectionary](https://github.com/yegor256/objectionary) extension of the EO language. Various collections will be implemented here, such as: sets, lists, maps, queues, etc.

## Collections

**What kind of objects actually exist in JAVA?**
- **ArrayList** - The implementation is based on an array. The size of the array can expand.


- **Vector** - A dynamic array that has the properties to expand and decrease.


- **LinkedList** - Doubly-linked list implementation.


- **Stack** - The Stack class represents a last-in-first-out (LIFO) stack of objects.


- **ArrayDeque** - A linear collection that supports element insertion and removal at both ends. Has no capacity limits.


- **PriorityQueue** - Provides a sorted priority queue. This implementation provides O(log(n)) time for the enqueuing and dequeuing methods (offer, poll, remove() and add); linear time for the remove(Object) and contains(Object) methods; and constant time for the retrieval methods (peek, element, and size).


- **Hashtable** - This class implements a hash table, which maps keys to values.


- **HashMap** - Hash table based implementation of the Map interface. The HashMap class is roughly equivalent to Hashtable, except that it is unsynchronized and permits nulls.


- **HashSet** - Set of unique unordered elements. This collection supports hash table logic.


- **LinkedHashSet** - This is an implementation of a unique set based on a doubly-linked list that has the property of ordering elements as they are added to the set.


- **LinkedHashMap** - Hash table and linked list implementation of the Map interface, with predictable iteration order.


- **TreeMap** - Red-black tree implementation. This implementation provides guaranteed log(n) time cost for the containsKey, get, put and remove operations.


- **TreeSet** - Tree with unique data set. This implementation provides guaranteed log(n) time cost for the basic operations (add, remove and contains).


Collections were examined for signs of their need for the EO language. From the research, it was concluded that it is necessary to implement the following objects:

## How to use array-list

This is how you can insert element of index in to **array-list**

```
+alias org.eolang.collection.array-list
+alias org.eolang.io.stdout
+alias org.eolang.txt.sprintf

array-list (* "baby" "mam" "dog" "cat") > arr
arr.insert "hello" 2
seq > @
  stdout "[ "
  arr.each
    [i]
      stdout
        sprintf
        "%s, "
        i
  stdout "]"
```

Output: ``[ baby, mam, hello, dog, cat, ]``

Simple manipulations:

```
# Make a new object list
+alias org.eolang.collection.array-list
array-list (* "baby" "mam" "dog" "cat") > arr

# return array with added element to end of array
arr.add "mouse"

# Get size of array
arr.size

# Return list without head
arr.insert "hello" 2

# Insert in list (first attribute is value second attribute is index)
arr.insert 10 3

# Get element for index
arr.get 2

# Return list without element of index
arr.remove 3

# Returns a view of the portion of this list between the specified fromIndex, inclusive, and toIndex, exclusive
arr.sub-list 0 2

# Appends all of the elements in the specified collection to the end of this list and return merged list
arr.add-all (* 1 2 3) (* 4 5 6)

```

## How to use list
The first collection that it was decided to create is **list**

This is how you can see second item in to **list**

```
+alias org.eolang.collection.list
+alias org.eolang.io.stdout
+alias org.eolang.txt.sprintf

list > lst
lst.push 5
lst.push 7
stdout > @
  sprintf
    "The second element value is %d"
    lst.get 1
```

Output: ``The second element value is 7``

Simple manipulations:

```
# Make a new object list
+alias org.eolang.cln.list
list > lst

# Add an element in front of the head
lst.push 20

# Get size list
lst.size

# Return list without head
lst.pop

# Insert in list (first attribute is value second attribute is index)
lst.insert 10 3

# Get element for index
lst.get 2

# Return list without element of index
lst.remove 3
```

## How to use set

This is how you can see create **set**

```
+alias org.eolang.collection.set
+alias org.eolang.io.stdout
+alias org.eolang.txt.sprintf

set 4 4 5 > s
  stdout > @
    sprintf
      "The first element is %d\n The second element is %d"
      s.get 0
      s.get 1
```

Output: 
```
The first element is 4
The second element is 5
```

Simple manipulations:

```
# Make a new object set
+alias org.eolang.cln.set
set 1 1 2 > s

# Get size set
s.size

# Is there an element "10" in the set
s.contains 10

# Add element in the set
s.add 5

# Return a set without element at index 1
s.remove 1

```

## How to use map

This is how you can see create **map**

```
+alias org.eolang.collection.map
+alias org.eolang.io.stdout
+alias org.eolang.txt.sprintf

pair "first" 1 > p1
pair "second" 2 > p2 
map p1 p2 > m
  stdout > @
    sprintf
      "The first value is %d\n The second value is %d"
      m.get "first"
      m.get "second"
```

Output:
```
The first value is 1
The second value is 2
```

Simple manipulations:

```
# Make a new object map
+alias org.eolang.cln.map
pair "first" 1 > p1
map p1 > m

# Get size map
m.size

# Is there an element "10" in the 
m.put pair "hello" 5

# Is there a key in the collection
m.contains.key "hello"

# Is there a value in the collection
m.contains.value 5

# Return all keys
m.keys

# Return all values
m.values

# Return a set without element at index 1
s.remove 1

```

## How to Contribute

Fork repository, make changes, send us a pull request.
We will review your changes and apply them to the `master` branch shortly,
provided they don't violate our quality standards. To avoid frustration,
before sending us your pull request please run full Maven build:

```bash
$ mvn clean install -Pqulice
```

You will need Maven 3.3+ and Java 8+.
