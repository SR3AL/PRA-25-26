# Summary ahead of the Second PRA Practice Exam 25/26
In this summary, we will cover the main concepts related to trees, including their structure, types, and traversal algorithms such as BFS and DFS.


## Trees

### Main Structure:

- Parent Node
- Child Nodes


> [!IMPORTANT]
> Child Nodes cannot be interconnected.

_Here you have an example of a basic tree structure:_

![tree_basicStructure](https://media.geeksforgeeks.org/wp-content/uploads/20221107210238/Capture1-660x440.JPG)

Tree's structure has a __root__ (parent node) and __leaf nodes__ (nodes that doesn't have any children).

### <ins>Types of trees</ins>

There are many types of trees.

- #### Regular Tree

  ![tree_RegularStructure](https://www.c-sharpcorner.com/article/tree-data-structure/Images/tree%201.jpg)

- #### Binary Tree

  ![tree_RegularStructure](https://miro.medium.com/v2/1*J6vjQJnrjVGkLyO7IpSulg.png)

> [!NOTE]
> Each child cannot have more than 2 child nodes.

- #### Binary Search Tree (BST)
    ![tree_BSTStructure](https://media.geeksforgeeks.org/wp-content/uploads/BST.png)

> [!NOTE]
> Each left child node must be less than the parent node, and each right child node must be greater than the parent node.
<br> <br>
### Coding Part

Each node consists of three main parts:
- Data
- Left Child Pointer
- Right Child Pointer

First, we need to create a class for the node structure:

```c++ 

class Node{
public:
    int data;
    Node* left;
    Node* right;

    Node(int val){
        data = val;
        left = nullptr;
        right = nullptr;
    }
};
```
Then, we can create functions to create nodes and insert values into the BST:

```c++
Node* createNode(int value){
    Node* newNode = new Node();
    newNode->data = value;
    newNode->left = nullptr;
    newNode->right = nullptr;
    return newNode; // We have to return the pointer to the newly created node
}
```

Now, we could create an example of a tree just like this:
```
        5
       / \
      3   7
     / \   \
    2   4   8
```

Just by using the `createNode` function:

```c++
Node* root = createNode(5);
root->left = createNode(3);
root->right = createNode(7);
root->left->left = createNode(2);
root->left->right = createNode(4);
root->right->right = createNode(8);
```

### Breadth-First Search (BFS)
BFS is an algorithm for traversing or searching tree or graph data structures. It starts at the tree root (or an arbitrary node of a graph) and explores the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level.
<br> <br>
For example, given the following tree:
```
        1
       / \
      2   3
     / \   \
    4   5   6
```
As you can see, the BFS traversal would visit the nodes in this order. <br>
This means that it works __level by level__, starting from the _root_ and moving down to the _leaves_.
<br> <br>

### Depth-First Search (DFS)
DFS is an algorithm for traversing or searching tree or graph data structures. It starts at the root (or an arbitrary node in the case of a graph) and explores as far as possible along each branch before backtracking.
<br> <br>
For example, given the following tree:
```
        1
       / \
      2   5
     / \   \
    3   4   6
```
As you can see, the DFS traversal would visit the nodes in this order. <br>
This means that it goes __as deep as possible down__ one path before _backtracking_ and _exploring_ other paths.
<br>

> [!IMPORTANT]
> BFS: priorizes width search
> DFS: priorizes depth search

#### <ins>Types of DFS(Depth-First Search Algorithms):</ins>
- Pre-order Traversal <span style = "color: orange">(Data -> Left -> Right)</span>
- In-order Traversal <span style = "color: orange">(Left -> Data -> Right)</span>
- Post-order Traversal <span style = "color: orange">(Left -> Right -> Data)</span>

> [!IMPORTANT]
> In order to understand better how each DFS algorithm works, it's recommended review how recursivity functions work.

Let's print the tree using <ins>pre-order traversal</ins>. For example, given the following tree:
```
          1
       /    \
      2      3
     / \    / \
    4   5  6   7
       /      /
      9      15
```
```c++
void printTree(Node* root){
    if(root == nullptr){
        return;
    }
    cout << root->data << endl; // Visit the root
    printTree(root->left);     // Traverse the left child
    printTree(root->right);    // Traverse the right child
}
```

Now, let's see how inorder traversal works. For example, given the following tree:
```
          1
       /    \
      2      3
     / \    / \
    4   5  6   7
       /      /
      9      15
```
```c++
void printTreeInOrder(Node* root){
    if(root == nullptr){
        return;
    }
    printTreeInOrder(root->left);     // Traverse the left child
    cout << root->data << endl;       // Visit the root
    printTreeInOrder(root->right);    // Traverse the right child
}
```

Post order traversal works like this. For example, given the following tree:
```
          1
       /    \
      2      3
     / \    / \
    4   5  6   7
       /      /
      9      15
```
```c++

void printTreePostOrder(Node*root){
    if(root == nullptr){
        return;
    }
    printTreePostOrder(root->left);     // Traverse the left child
    printTreePostOrder(root->right);    // Traverse the right child
    cout << root->data << endl;         // Visit the root
}
```

### Author:
- **Name**: Sergio Real Gonzalvo
- **Email**: sergiete.real@gmail.com
