- A binary tree is full when every item points to two nodes or 0 nodes.
- A prefect tree is when all the lines are filled with nodes without missing a node.
-  A binary tree is complete when all levels are fully filled except possibly the last, and in the last level, nodes are as far left as possible.
- Best possible scenario is O(log n), worst possible scenario O(n) for Binary tree.


# Binary Search Tree (BST) Implementation

## Overview
This code provides an implementation of a **Binary Search Tree (BST)** in JavaScript. It allows for efficient insertion, searching, and finding the minimum value in a tree. The tree follows the binary search tree property: the left child node contains a smaller value, and the right child node contains a larger value.

## Code

```js
class Node {
    constructor(value) {
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BST {
    constructor() {
        this.root = null;
    }

    insert(value) {
        const new_node = new Node(value);
        if(this.root === null) {
            this.root = new_node;
            return this;
        }

        let temp = this.root;

        while(true) {
           if(new_node.value === temp.value) return undefined;

            if(new_node.value < temp.value) {
                if(temp.left === null) {
                    temp.left = new_node;
                    return this;
                }
                temp = temp.left;
            }

            else {
                if(temp.right === null) {
                    temp.right = new_node;
                    return this;
                }
                temp = temp.right;
            }
        }
    }

    contains(value) {
        if(this.root === null) {
            return false;
        }

        let temp = this.root;

        while(temp) {
            if(value < temp.value) {
                temp = temp.left;
            }

            else if(value > temp.value) {
                temp = temp.right;
            }

            else {
                return true;
            }
        }

        return false;
    }

    findMinValue(currentNode) {
        while(currentNode.left) {
            currentNode = currentNode.left;
        }
        return currentNode;
    }
}

const myBST = new BST();
myBST.insert(17);
myBST.insert(15);
myBST.insert(25);
myBST.insert(22);
myBST.insert(35);
myBST.insert(13);
myBST.insert(16);

myBST.findMinValue(myBST.root.right);
```

## Classes and Methods

### 1. **Node**
Represents a node in the BST.
- **Properties:**
  - `value`: Value stored in the node.
  - `left`: Left child node (smaller value).
  - `right`: Right child node (larger value).

#### Constructor:
```js
constructor(value)
```
- Initializes the node with a given value, setting `left` and `right` to `null`.

### 2. **BST (Binary Search Tree)**
Handles the BST structure and operations like insertion, search, and finding the minimum value.

#### Constructor:
```js
constructor()
```
- Initializes the root of the tree to `null`.

#### Methods:

- **insert(value):**  
  Inserts a new node into the tree.
  - Traverses the tree to find the correct position for the new node.
  - Inserts it to the left (if smaller) or right (if larger) of the current node.

- **contains(value):**  
  Checks if a value exists in the tree.
  - Traverses the tree to search for the given value.

- **findMinValue(currentNode):**  
  Finds the node with the smallest value in the subtree starting from `currentNode`.
  - Repeatedly moves to the left child until no further left children exist.

## Example Usage:

```js
const myBST = new BST();
myBST.insert(17);
myBST.insert(15);
myBST.insert(25);
myBST.insert(22);
myBST.insert(35);
myBST.insert(13);
myBST.insert(16);

myBST.findMinValue(myBST.root.right);  // Finds the smallest value in the right subtree.
```

## Time Complexity
- **Insert**: O(log n) on average.
- **Search (contains)**: O(log n) on average.
- **Find Min Value**: O(log n).


