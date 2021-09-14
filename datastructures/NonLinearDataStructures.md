# Non-Linear Data Structures

## Binary Trees

* Overview
  * Stores elements in a hierarchy
  * Element = Nodes
  * Lines = Edges
  * Top of tree element = Root
  * Each node has two elements in binary tree (max = 2)
  * Bottom of tree, nodes without children are called Leaf
* Examples
  * Represent hierarchical data
  * Databases (indexing)
  * Autocompletion
  * Compilers
  * Compression (JPEG)

### Binary Search Tree

* Left < Node < Right
  * Subtree on left, less than value of root
  * Subtree on right, greater than value of root
* Logarithmic Time - O(log n)

#### insert - O (log n)

```java
public class Tree {
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;
  
  public void insert(int value) {
    var node = new Node(value);
    
    if (root == null) {
      root = new Node(value);
      return;
    }
    
    var current = root;
    while (true) {      
      if (value < current.value) {
        if (current.leftChild == null) {
          current.leftChild = node;
          break;
        }
        current = current.leftChild;
      }
      else {
        if (current.rightChild == null) {
          current.rightChild = node;
          break;
        }
        current = current.rightChild;
      }
    }
  }
}
```

#### find - O (log n)

```java
public class Tree {
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
  }
  
  private Node root;
  
  public boolean find(int value) {
    var current = root;
    
    while (current != null) {
      if (value < current.value)
        current = current.leftChild;
      else if (value > current.value)
        current = current.rightChild;
      else
        return true;
    }
    
    return false;
  }
}
```

### Tree Traversal

* Breadth First
  * Level Order
* Depth First
  * Pre-order (Root, Left, Right)
    * e.g. [1, 4, 6, 7 (root), 8, 9, 10] -> [7, 4, 1, 6, 9, 8, 10]
  * In-order (Left, Root, Right)
    * e.g.  [1, 4, 6, 7 (root), 8, 9, 10] -> [1, 4, 6, 7, 8, 9, 10]
    * To reverse, just visit Right, Root, Left
  * Post-order (Left, Right, Root)
    * e.g. [1, 4, 6, 7 (root), 8, 9, 10] -> [1, 6, 4, 8, 10, 9, 7]
    * Traverse leaf nodes first

### Recursion

#### Using iteration

```java
public static int factorial(int n) {
  var factorial = 1;
  for (var i = n; i > 1; i--)
    factorial *= i;
  return factorial;
}
```

#### Using recursion

* recursive method is when method calls itself
* Base conditions terminate recursive methods
* Java uses stacks to manage recursive calls

```java
public static int factorial (int n) {
  if (n == 0)
    return 1;
  
  return n * factorial(n - 1);
}
```

### Depth First Traversals - PreOrder

```java
public class Tree {
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;
  
  public void traversePreOrder() {
    traversePreOrder(root);
  }
  
  private void traversePreOrder(Node root) {
    if (root == null)
      return;
    
    System.out.println(root.value);
    traversePreOrder(root.leftChild);
    traversePreOrder(root.rightChild);
  }
}
```

### Depth and Height of Nodes

* Depth = number of edges from root to node
* Height = number of edges from leaf to parent node
  * e.g. `height = 1 + max(height(L), height(R))`
  * Use post order traversal to calculate height of node

```java
public class Tree {
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;
  
  public int height() {
    return height(root);
  }
  
  private void height(Node root) {
    if (root == null)
      return -1;
    
    if (isLeaf(root))
      return 0;
    
    return 1 + Math.max(height(root.leftChild), height(root.rightChild));
  }
  
  private boolean isLeaf(Node node) {
    return root.leftChild == null && root.rightChild == null;
  }
}
```

### Minimum Value in a Tree

* Need to figure out if you're dealing with Binary Tree vs Binary Search Tree
  * If you're using a BST, need to find left-most leaf

#### Binary Tree

```java
public class Tree {
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;
  
  public int min() {
    return min(root);
  }
  
  // O(n) - have to traverse every node in tree
  private int min(Node root) {
    if (isLeaf(root))
      return root.value;
    
    var left = min(root.leftChild);
    var right = min(root.rightChild);
    
    return Math.min(Math.min(left, right), root.value);
  }
  
  private boolean isLeaf(Node node) {
    return root.leftChild == null && root.rightChild == null;
  }
}
```

#### Binary Search Tree

```java
public class Tree {  
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;

  // O(log n) - we throw out half of nodes when searching
  public int min() {
    if (root == null)
      throw new IllegalStateException();
    
    var current = root;
    var last = current;
      
    while (current != null) {
      last = current;
      current = current.leftChild;
    }
    
    return last.value;
  }
}
```

### Equality Checking

* Using pre-order traversal

```java
public class Tree {  
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;

  public boolean equals(Tree other) {
    if (other == null)
      return false;
    
    return equals(root, other.root);
  }
  
  private boolean equals(Node first, Node second) {
    if (first == null && second == null)
      return true;
    
    if (first != null && second != null)
      return first.value == second.value && equals(first.leftChild, second.leftChild) && equals(first.rightChild, second.rightChild);
    
    return false;
  }
}
```

### Validating BST

* Check to see if Tree is BST
* Can use recursion to visit every node, but is costly
  * Will visit each node multiple times
* Traverse every node in tree and check if value of node is in right range
  * Root (-INF, +INF)
  * Left (outter most edge) (-INF, parent.value)
  * Left (inner most edge) (parent.value, parent.parent.value)
  * Right (outter most edge) (parent.value, +INF)
  * Right (inner most edge) (parent.parent.value, parent)
* Utilizing pre-order traversal because we validate root first, then left, then right

```java
public class Tree {  
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;

  public boolean isBST() {
    return isBST(root, Integer.MIN_VALUE, Integer.MAX_VALUE);
  }
  
  private boolean isBST(Node root, int min, int max) {
    if (root == null)
      return true;
    
    if (root.value < min || root.value > max)
      return false;
    
    return isBST(root.leftChild, min, root.value - 1) && isBST(root.rightChild, root.value + 1, max);
  }
}
```

```java
// Use to change BST to BT
public void swapRoot() {
  var temp = root.leftChild;
  root.leftChild = root.rightChild;
  root.rightChild = temp;
}
```

### Nodes at K Distance

* When thinking of Trees, always think of recursion
* Think of easiest solution first, then break down problem

```java
public class Tree {  
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;

  public ArrayList<Integer> getNodesAtDistance(int distance) {
    var list = new ArrayList<Integer>();
    getNodesAtDistance(root, distance, list);
    return list;
  }
  
  private void getNodesAtDistance(Node root, int distance, ArrayList<Integer> list) {
    if (root == null)
      return;
    
    if (distance == 0) {
      list.add(root.value);
      return;
    }
    
    getNodesAtDistance(root.leftChild, distance - 1, list);
    getNodesAtDistance(root.rightChild, distance - 1, list);
  }
}
```

### Level Order Traversal

* Go level-by-level
* We need to know how many levels we have, e.g. `height` property
* The height tree equals to height of root node, i.e. number of edges to longest path to leaf node

```java
public class Tree {  
  private class Node {
    private int value;
    private Node leftChild;
    private Node rightChild;
    
    public Node(int value) {
      this.value = value;
    }
  }
  
  private Node root;

  public void traverseLevelOrder() {
    for (var i = 0; i <= height(); i++)
      for (var value : getNodesAtDistance(i))
        System.out.println(value);
  }
  
  public int height() {
    return height(root);
  }
  
  public ArrayList<Integer> getNodesAtDistance(int distance) {
    var list = new ArrayList<Integer>();
    getNodesAtDistance(root, distance, list);
    return list;
  }
  
  private void getNodesAtDistance(Node root, int distance, ArrayList<Integer> list) {
    if (root == null)
      return;
    
    if (distance == 0) {
      list.add(root.value);
      return;
    }
    
    getNodesAtDistance(root.leftChild, distance - 1, list);
    getNodesAtDistance(root.rightChild, distance - 1, list);
  }
  
  private void height(Node root) {
    if (root == null)
      return -1;
    
    if (isLeaf(root))
      return 0;
    
    return 1 + Math.max(height(root.leftChild), height(root.rightChild));
  }
}
```

## AVL Trees

### Balanced and Unbalanced Trees

* Balanced trees = `height(left) - height(right) <= 1`
* Right Skewed and Left Skewed (skew trees are the worst BSTs)
* Trees can become skewed when values are inserted as sorted values (ASC or DSC)
* Self-balancing tress
  * AVL Trees (Adelson-Velsky and Landis)
  * Red-black Trees
  * B-trees
  * Splay Trees
  * 2-3 Trees

### Rotations

* AVL trees balance themselves by using rotations when height of left and right nodes are greater than 1
* 4 types
  * Left (LL)
  * Right (RR)
  * Left-Right (LR)
  * Right-Left (RL)
* Always start with last node added (height = 0)
* If tree is heavy on right, we need to apply a left rotation, etc
* e.g. Insert [30, 15, 18] - left skewed tree
  * Insertion order
    * 30 = (left height = 2, right height = 0)
    * 15 = (0, 1)
    * 18 = (0, 0)
  * Step 1: rotate 15 to left, bring 18 down (tree imbalance is in left child, right sub tree - LR)
    * 30 = (2, 0)
  * Step 2: rotate 30 to right, bring 30 down, move 18 up
  * Step 3: add 10 (tree is balanced)
  * Step 4: add 16 (tree is balanced)
  * Step 5: add 7 (tree is unbalanced - imbalance is in left child, left subtree - RR)
    * 18 = (3, 1)
  * Step 6: rotate 18 to right, bring 15 up, disconnect 16 and bring 16 down
  * Step 7: bring 18 down with 30 (tree is balanced)
  * Step 8: 16 is greater than 15, but less than 18, so attach to 18 as left child
  * Step 9: add 8 (tree is unbalanced - imbalance is in left child, right subtree - LR)
    * 10 = (2, 0)
  * Step 10: rotate 7 to right, bring 8 up
  * Step 11: bring 10 down, move 7 up

