# Linear Data Structures

## Arrays

### Operations

#### insert - O(1)

```java
public class Array {
  private int[] items;
  private int count;
  
  public Array(int length) {
    items = new int[length];
  }
  
  public void insert(int item) {
    // If the array is full, resize it
    if (items.length == count)
      // Create a new array (twice the size)
      int[] newItems = new int[count*2];
    
    // Runtime complexity: 0(n)
    
    // Copy all of the existing items
    for (int i = 0; i < count; i++)
      newItems[i] = items[i];
    
    // Set "items" to this new array
    items = newItems;
    
    // Add the new item at the end
    items[count++] = item;
  }
}
```

#### removeAt - O(n)

```java
public class Array {
  private int[] items;
  private int count;
  
  public Array(int length) {
    items = new int[length];
  }
  
  public void removeAt(int index) {
    // Validate the index
    if (index < 0 || index >= count)
      throw new NoSuchElementException();
    
    // Runtime complexity: 0(n)
    
    // Shift the items to the left to fill the hole
    // index: 1
    // 1 <- 2
    // 2 <- 3
    for (int i = index; i < count; i++)
      items[i] = items[i + 1];
    
    // Decrement the total number of elements in the array
    count--;
  }
}
```

#### indexOf - O(1) or O(n)

```java
public class Array {
  private int[] items;
  private int count;
  
  public Array(int length) {
    items = new int[length];
  }
  
  public void indexOf(int item) {
    // If we find it, return index
    // Otherwise, return -1
    
    // Worst case runtime: 0(n) - we iterate all the way to the end of the array
    // Best case runtime: 0(1) - the item we're looking for is at the beginning
    for (int i = 0; i < count; i++)
      if (items[i] == item)
        return i;
    
    return -1;
  }
}
```



## Linked Lists

### Operations

#### addLast - O(1)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void addLast(int item) {
    // Create new node
    var node = new Node(item);
    
    // Check if it's empty, if so, set first and last to item
    // Otherwise set the next node to the item and set last to item
    if (isEmpty()) {
      first = last = node;
    } else {
      last.next = node;
      last = node;
    }
  }
  
  private boolean isEmpty() {
    if (first == null) return false;
  }
}
```

#### addFirst - O(1)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void addFirst(int item) {
    var node = new Node(item);
    
    if (isEmpty()) {
      first = last = node;
    } else {
      node.next = first;
      first = node;
    }
  }
  
  private boolean isEmpty() {
    if first == null;
  }
}
```

#### indexOf - O(n)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public int indexOf(int item) {
    int index = 0;
    var current = first;
    
    while (current != null) {
      if (current.value == item)
        return index;
    	current = current.next;
    	index++;
    }
    
    return -1;
  }
}
```

#### contains - O(n)

```java
public class LinkedList {  
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void indexOf(int item) {
    int index = 0;
    var current = first;
    
    while (current != null) {
      if (current.value == item)
        return index;
    	current = current.next;
    	index++;
    }
    
    return -1;
  }
  
  public boolean contains(int item) {
    return indexOf(item) != -1;
  }
}
```

#### removeFirst - O(1)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void removeFirst() {
    // Edge case #1: if the list is empty, throw exception
    if (isEmpty())
      throw new NoSuchElementException();
    
    // Edge case #2: if list only has single item
    if (first == last) {
      first = last = null;
      return;
    }
    
    var second = first.next;
    first.next = null;
    first = second;
  }
  
   private boolean isEmpty() {
    if first == null;
  }
}
```

#### removeLast - O(n)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void removeLast() {
    // Edge case #1: if the list is empty, throw exception
    if (isEmpty())
      throw new NoSuchElementException();
    
    // Edge case #2: if list only has single item
    if (first == last) {
      first = last = null;
      return;
    }
    
    var previous = getPrevious(last);
    last = previous;
    last.next = null;
  }
  
  private Node getPrevious(Node node) {
    var current = first;
    
    while (current != null) {
      if (current.next == node)
        return current;
      current = current.next;
    }
    
    return null;
  }
  
  private boolean isEmpty() {
    if first == null;
  }
}
```

#### size - O(1)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  private int size;
  
  public void addFirst(int item) {
    var node = new Node(item);
    
    if (isEmpty()) {
      first = last = node;
    } else {
      node.next = first;
      first = node;
    }
    
    size++;
  }
  
 	public void addLast(int item) {
    var node = new Node(item);
    
    if (isEmpty()) {
      first = last = node;
    } else {
      last.next = node;
      last = node;
    }
    
    size++;
  }
  
  public void removeFirst() {
    if (isEmpty())
      throw new NoSuchElementException();
    
    if (first == last)
      first = last = null;
    else {
      var second = first.next;
      first.next = null;
      first = second; 
    }
    
    size--;
  }
  
  public void removeLast() {
    if (isEmpty())
      throw new NoSuchElementException();
    
    if (first == last)
      first = last = null;
    else {
      var previous = getPrevious(last);
      last = previous;
      last.next = null;
    }
    
    size--;
  }
  
  private Node getPrevious(Node node) {
    var current = first;
    
    while (current != null) {      
      if (current.next == node)
        return current;
      current = current.next;
    }
    
    return null;
  }
  
  private boolean isEmpty() {
    if (first == null) return false;
  }
  
  // Runtime complexity: O(1)
  public int size() {
    return size;
  }
  
  private boolean isEmpty() {
    if first == null;
  }
}
```

#### toArray - O(n)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  private int size;
  
  public int[] toArray() {
    int[] array = new int[size];
    var current = first;
    var index = 0;
    
    while (current != null) {
      array[index++] = current.value;
      current = current.next;
    }
    
    return array;
  }
  
  public int size() {
    return size;
  }
}
```

### Arrays vs Linked Lists

* Space
  * Static vs Dynamic
    * Static arrays have a fixed size
    * Dynamic arrays grow by 50-100%
  * Arrays are great when you know how many items you have
  * Linked lists don't waste memory
    * However they take extra memory, each node stores an address to the next node
* Time:

| Operation              | Arrays | Linked Lists |
| ---------------------- | :----: | :----------: |
| Lookup (by index)      |  O(1)  |     O(n)     |
| Lookup (by value)      |  O(n)  |     O(n)     |
| Insert (beginning/end) |  O(n)  |     O(1)     |
| Insert (middle)        |  O(n)  |     O(n)     |
| Delete (beginning)     |  O(n)  |     O(1)     |
| Delete (middle)        |  O(n)  |     O(n)     |
| Delete (end)           |  O(n)  |     O(n)     |

### Types of Linked Lists

* Singly
  * Delete from end: O(n)
* Doubly
  * Delete from end: O(1)
  * Take more space than singly linked lists
* Circular
  * Both singly and doubly linked lists

### reverse - O(n)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  
  public void reverse() {
    // Validation
    if (isEmpty())
      return;
    
    // Set previous and current from first and next reference
    var previous = first;
    var current = first.next;
    
    // Change direction of reference
    while (current != null) {
      var next = current.next;
    	current.next = previous;
      previous = current;
      current = next;
    }
    
    // Swap last and first nodes
    last = first;
    last.next = null;
    first = previous;
  }
  
  private boolean isEmpty() {
    if first == null;
  }
}
```

### getKthFromTheEnd - O(n)

```java
public class LinkedList {
  private class Node {
    private int value;
    private Node next;
  }
  
  private Node first;
  private Node last;
  private int size;
  
  public int getKthFromTheEnd(int k) {
    // Assumes we know the size
    int m = size;
    
    if (m == 0)
      throw new IllegalStateException();
    
    if (k > m)
      throw new IllegalArgumentException();
    
    var current = first;
    
    while (m != k) {
      current = current.next;
      m--;
    }
    
    return current.value;
  }
  
  private boolean isEmpty() {
    if first == null;
  }
}
```

## Stacks

* Examples
  * Implement undo feature
  * Build compilers (syntax checking)
  * Evaluate expressions
  * Build navigation (eg forward/back)
* Last In First Out (LIFO)
* Wrapper around Array or LinkedList
* Don't have lookups because that's not their use case

### Operations

#### push(item) - O(1)

```java
public class Stack {
  private int[] items;
  private int count;
  
  public Stack(int size) {
    items = new int[size];
  }
  
  public void push(int item) {
    if (count == items.length)
      throw new StackOverflowError();
    items[count++] = item;
  }
}
```

#### pop - O(1)

```java
public class Stack {
  private int[] items;
  private int count;
  
  public Stack(int size) {
    items = new int[size];
  }
  
  public int pop() {
    if (count == 0)
      throw new IllegalStateException();
    return items[--count];
  }
}
```

#### peek - O(1)

```java
public class Stack {
  private int[] items;
  private int count;
  
  public Stack(int size) {
    items = new int[size];
  }
  
  public int peek() {
    if (count == 0)
      throw new IllegalStateException();
    return items[count - 1];
  }
}
```

#### isEmpty - O(1)

```java
public class Stack {
  private int[] items;
  private int count;
  
  public Stack(int size) {
    items = new int[size];
  }
  
  public boolean isEmpty() {
    return count == 0;
  }
}
```

#### toString - O(n)

```java
public class Stack {
  private int[] items;
  private int count;
  
  public Stack(int size) {
    items = new int[size];
  }
  
  @Override
  public String toString() {
    var content = Arrays.copyOfRange(items, 0, count);
    return Arrays.toString(content);
  }
}
```



### Reversing a String

```java
public class StringReverser {
  public String reverse(String input) {
    if (input == null)
      throw new IllegalArgumentException();
    
    Stack<Character> stack = new Stack<>();
    
    for (char ch : input.toCharArray())
      stack.push(ch);
    
    StringBuffer reversed = new StringBuffer();
    
    while (!stack.empty())
      reversed.append(stack.pop());
    
    return reversed.toString();
  }
}
```

### Balanced Expressions

```java
public class ExpressionValidator {
  private final List<Character> leftBrackets = Arrays.asList('(', '[', '{', '<');
  private final List<Character> rightBrackets = Arrays.asList(')', ']', '}', '>');
  
  public boolean isBalanced(String input) {
    if (input == null)
      throw new IllegalArgumentException();
    
    Stack<Character> stack = new Stack<>();
    
    for (char ch : input.toCharArray())
      if (isLeftBracket(ch))
      	stack.push(ch);
    
    	if (isRightBracket(ch)) {
        if (stack.empty())
          return false;
    
    		char top = stack.pop();
        if (!bracketsMatch(ch, top))
          return false;
      }
    
    return stack.empty()
  }
  
  private boolean isLeftBracket(char ch) {
    return leftBrackets.contains(ch);
  }
  
  private boolean isRightBracket(char ch) {
    return rightBracket.contains(ch);
  }
  
  private boolean bracketsMatch(char left, char right) {
    return leftBrackets.indexOf(left) == rightBrackets.indexOf(right);
  }
}
```

## Queues

* First-in First-out (FIFO)
* Sharing a resource amongst many consumers
* Examples
  * Printers
  * Operating systems
  * Web servers
  * Live support systems
* Queue class in Java are interfaces (cannot be instantiated)
  * Interfaces are "contracts"
  * Most common Java implementations are *ArrayDeque* (double ended queue), *LinkedList*
* 3 ways to implement a queue
  * Array, LinkedList, Stack

### Operations

#### enqueue - O(1)

```java
public class ArrayQueue {
  private int[] items;
  private int front;
  private int rear;
  private int count;
  
  public ArrayQueue(int size) {
    items = new int[size];
  }
  
  public void enqueue(int item) {
    if (count == items.length)
      throw new IllegalStateException();
    items[rear] = item;
    rear = (rear + 1) % items.length; // Circular Array index implementation
    count++;
  }
  
  @Override
  public String toString() {
    var content = Arrays.copyOfRange(items, 0, count);
    return Arrays.toString(content);
  }
}
```

#### dequeue - O(1)

```java
public class ArrayQueue {
  private int[] items;
  private int front;
  private int rear;
  private int count;
  
  public ArrayQueue(int size) {
    items = new int[size];
  }
  
  public int dequeue() {
    var item = items[front];
    items[front] = 0;
    front = (front + 1) % items.length; // Circular Array index implementation
    count--;
    return item;
  }
  
  @Override
  public String toString() {
    var content = Arrays.copyOfRange(items, 0, count);
    return Arrays.toString(content);
  }
}
```

#### peek - O(1)

#### isEmpty - O(1)

#### isFull - O(1)

### Reversing a queue

* Only allowed to use `add`, `remove`, `isEmpty` methods

```java
public class Main {
  public static void main(String[] args) {
    Queue<Integer> queue = new ArrayDeque<>();
    queue.add(10);
    queue.add(20);
    queue.add(30);
    reverse(queue);
  }
  
  public static void reverse(Queue<Integer> queue) {
    Stack<Integer> stack = new Stack<>();
    
    while (!queue.isEmpty())
      stack.push(queue.remove());
    
    while (!stack.isEmpty())
      queue.add(stack.pop());
  }
}
```

### Implementing a queue using a stack

```java
public class StackQueue {
  private Stack<Integer> enqueue = new Stack<Integer>();
  private Stack<Integer> dequeue = new Stack<Integer>();
  
  // O(1)
  public void enqueue(int item) {
    enqueue.push(item);
  }
  
  // O(n)
  public int dequeue() {
    if (isEmpty())
      throw new IllegalStateException();
    
    moveStack();
    
    return dequeue.pop();
  }
  
  public int peek() {
    if (isEmpty())
      throw new IllegalStateException();
    
    moveStack();
    
    return dequeue.peek();
  }
  
  private void moveStack() {
    if (dequeue.isEmpty())
      while (!enqueue.isEmpty())
        dequeue.push(enqueue.pop());
  }
  
  public boolean isEmpty() {
    return enqueue.isEmpty() && dequeue.isEmpty();
  }
  
  @Override
  public String toString() {
    var content = Arrays.copyOfRange(items, 0, count);
    return Arrays.toString(content);
  }
}
```

### Priority Queues

* Objects are processed based on their priority, not their order
* 2 types of implementations
  * Arrays, Heap

```java
public class PriorityQueue {
  int[] items;
  private int count;
  
  public PriorityQueue(int size) {
    items = new int[size];
  }
  
  // O(n)
  public void enqueue(int item) {
    if (isFull())
      throw new IllegalStateException();
    int i = shiftItemsToInsert(item);    
    items[i] = item;
    count++;
  }
  
  private int shiftItemsToInsert(int item) {
    int i;
    for (i = count - 1; i >= 0; i--) {
      if (items[i] > item)
        items[i + 1] = items[i];
      else
        break;
    }
    return i + 1;
  }
  
  public int dequeue() {
    if (isEmpty())
      throw new IllegalStateException();
    return items[--count];
  }
  
  public boolean isFull() {
    return count == items.length;
  }
  
  public boolean isEmpty() {
    return count == 0;
  }
  
  @Override
  public String toString() {
    var content = Arrays.copyOfRange(items, 0, count);
    return Arrays.toString(content);
  }
}
```

## Hash Tables

* Examples
  * Spell checkers
  * Dictionaries
  * Compilers
  * Code editors
* (key, value) pairs
  * Hash function determines where object should be stored/retrieved in memory
* Deterministic
  * Same input will always return same value
* Hash Table utilizes Array to store values
* Allows null for key and values
* Sets
  * Only have keys
  * Don't allow duplicate keys

### Operations

#### put - O(1)

```java
public class HashTable {
  private class Entry {
    private int key;
    private String value;
    
    public Entry(int key, String value) {
      this.key = key;
      this.value = value;
    }
  }
  
  private LinkedList<Entry>[] entries;
  private int size;
  
  public HashTable(int size) {
    entries = new LinkedList[size];
  }
  
  public void put(int key, String value) { 
    var entry = getEntry(key);
    if (entry != null) {
      entry.value = value;
      return;
    }
    
    getOrCreateBucket(key).add(new Entry(key, value));
  }
  
  private LinkedList<Entry> getOrCreateBucket(int key) {
    var index = hash(key);
    var bucket = entries[index];
    if (bucket == null)
      entries[index] = new LinkedList<>();
    
    return bucket;
  }
  
  private Entry getEntry(int key) {
    var index = hash(key);
    var bucket = getBucket(key);
    
    if (bucket != null) {
      for (var entry: bucket) {
        if (entry.key == key)
          return entry;
      }
    }
    
    return null;
  }
  
  private int hash(int key) {
    return key % size;
  }
}
```

#### get - O(1)

```java
public class HashTable {
  private class Entry {
    private int key;
    private String value;
    
    public Entry(int key, String value) {
      this.key = key;
      this.value = value;
    }
  }
  
  private LinkedList<Entry>[] entries;
  private int size;
  
  public HashTable(int size) {
    entries = new LinkedList[size];
  }
  
  public String get(int key) {
    var entry = getEntry(key);
    return (entry == null) ? null : entry.value;
  }
  
  private LinkedList<Entry> getBucket(int key) {
    return entries[hash(key)];
  }
  
  private Entry getEntry(int key) {
    var index = hash(key);
    var bucket = getBucket(key);
    
    if (bucket != null) {
      for (var entry: bucket) {
        if (entry.key == key)
          return entry;
      }
    }
    
    return null;
  }
  
  private int hash(int key) {
    return key % size;
  }
}
```

#### remove - O(1)

```java
public class HashTable {
  private class Entry {
    private int key;
    private String value;
    
    public Entry(int key, String value) {
      this.key = key;
      this.value = value;
    }
  }
  
  private LinkedList<Entry>[] entries;
  private int size;
  
  public HashTable(int size) {
    entries = new LinkedList[size];
  }
  
  public void remove(int key) {
    var entry = getEntry(key);
    if (entry == null)
      throw new IllegalStateException();
    getBucket(key).remove(entry);
  }
  
  private LinkedList<Entry> getBucket(int key) {
    return entries[hash(key)];
  }
  
  private Entry getEntry(int key) {
    var index = hash(key);
    var bucket = getBucket(key);
    
    if (bucket != null) {
      for (var entry: bucket) {
        if (entry.key == key)
          return entry;
      }
    }
    
    return null;
  }
  
  private int hash(int key) {
    return key % size;
  }
}
```

#### containsKey - O(1)

#### containsValue - O(n)

### Find first non-repeated character

```java
public class CharFinder {
  public char findFirstNonRepeatedCharacter(String input) {
    Map<Character, Integer> map = new HashMap<>();
    
    char[] charArray = input.toCharArray();
    
    for (var ch : charArray) {
      var count = map.containsKey(ch) ? map.get(ch) : 0;
      map.put(ch, count + 1);
    }
    
    for (var ch : charArray)
      if (map.get(ch) == 1)
        return ch;
    
    return Character.MIN_VALUE;
  }
}
```

### Find first repeated character

```java
public class CharFinder {
  public char findFirstRepeatedCharacter(String input) {
    Set<Character> set = new HashSet<>();
    
    for (var ch : input.toCharArray()) {
      if (set.contains(ch))
        return ch;
      
      set.add(ch);
    }
    
    return Character.MIN_VALUE;
  }
}
```

### Hash Functions

* Function that gets a value and maps to different kind of value (hash value, hash code, etc)
  * Maps (key, value) to index value
* Hash function for integer keys utilizes `%` modulus operator to find the remainder of the division between number and size of array
* For Strings, we iterate over characters and implicitly cast to integer hash and then apply the modulus operator
* In Java, every object has `hashCode` method

### Collisions

* When generating hash values, it's possible that two distinct keys generate the same hash value

* A collision is when we try to store two items at the same index

* Two ways to handle collisions

  * Each cell in our array point to a linked list (we don't store the values in the array itself), called ***chaining***

    * If you have a collision, we simply add the new item at the end of a linked list

    * slots in memory are called buckets/slots (all are initialized as null or empty)

    * e.g.

      ```
      1. we have HashTable(n=5)
      2. we want to insert (6, A)
      3. index = 6 % 5 = 1
      4. wrap in linked list
      5. [0, 1 -> LinkedList(A), 2, 3, 4]
      6. we want to insert (8, B)
      7. index = 8 % 5 = 3
      8. [0, 1 -> LinkedList(A), 2, 3 -> LinkedList(B), 4]
      9. we want to insert (11, C)
      10. index = 11 % 5 = 1 **collision**
      11. [0, 1 -> LinkedList(A) -> LinkedList(C), 2, 3 -> LinkedList(B), 4]
      ```

  * Another solution is to find a different slot for storing the second value. This is called ***open addressing***. We find a new address to store the value. We search for another location, called ***probing***.

    * Linear probing
      * Go forward until we find an empty slot
        * `index = hash(key) + i % table_size`
      * Drawbacks
        * If hash table is full, can't find another address
        * Clusters are created which means it takes longer to find empty address
    * Quadratic probing
      * Solves clustering
        * `index = hash(key) + i^2 % table_size`
      * Drawbacks
        * Infinite loops might occur because algorithm generates the same steps
    * Double hashing
      * Solves infinite loops
        * `hash2(key) = prim - (key % prime)`
        * `index = (hash1(key) + i * hash2(key)) % table_size`

