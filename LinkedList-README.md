# Summary ahead of the Second PRA Practice Exam 25/26

Here you'll find a summary of all about Linked Lists, disadvantages, advantages in front of arrays. <br> This is a theoretical summary where you'll find the main concepts with detailed explanations and examples to help you understand better this data structure.

## Linked Lists
A _Linked List_ is a linear data structure where elements, called nodes, are stored in a sequence. 

Each node contains two main components: **data** and a **pointer to the next node** in the sequence. 

Unlike _Arrays_, Linked Lists do not require contiguous memory allocation, allowing for **dynamic memory usage** and efficient insertions and deletions.

### Main Structure:

As I said before, a Linked List is made up of <ins>**nodes**</ins>. Each node has two parts:
- **Value**: This part stores the actual data or value of the node.
- **Pointer**: This part stores the address of the next node in the list.

![img_nodeStructure](https://www.alphacodingskills.com/imgfiles/linked-list-node.PNG)

To create a ```Node```, we can define a simple class in C++:

```c++
class Node{
    public:
        int Value; // Data part
        Node* Next; // Pointer part
};
```
Then, if we would want to assign values to the node, we could do it like this:

```c++
int main(){
    Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();

    head->Value = 1;
    head->Next = second;
    second->Value = 2;
    second->Next = third;
    third->Value = 3;
    third->Next = nullptr;
}
```

To access the values of the nodes, we can create a function that prints all the values in the Linked List:

```c++
void printList(Node* n){
    while(n != nullptr){
        std::cout << n->Value << std::endl;
        n = n->Next;
    }
}
```

### How to insert a new node in a Linked List

There are <ins>three main ways</ins> to insert a new node in a Linked List:
1.  At the front
2.  At the end
3.  After a given node

### 1. Inserting at the front
To insert a new node **at the front** of the Linked List, we need to:
1. Prepare a new node
2. Put it in front of the current head
3. Move head of the list to point to the newNode

![img_insertAtFront](https://media.geeksforgeeks.org/wp-content/uploads/20240222162726/Insertion-at-the-Beginning-of-Singly-Linked-List.webp)

How you can implement it in C++:
```c++
void insertAtFront(Node** head, int newValue){
    Node* newNode = new Node(); // Prepare a new node
    new Node -> Value = newValue; 
    newNode -> Next = *head; // Put it in front of the current head
    *head = newNode; // Move head of the list to point to the newNode
}
```

For inserting the call of the function ``insertAtFront`` would be like this: 
```c++
insertAtFront(&head, 15); // This will insert a new node with value 15 at the front
```

### 2. Inserting at the end
To insert a new node **at the end** of the Linked List, we need to:
1. Prepare a newNode
2. If Linked List is empty, then make the newNode as head
3. Find the last node
4. Insert newNode after the last node(at the end)

![img_insertAtEnd](https://media.geeksforgeeks.org/wp-content/uploads/20240222162837/Insertion-at-the-End-of-Singly-Linked-List.webp)

How you can implement it in C++:
```c++
void insertAtEnd(Node** head, int newValue){
    Node* newNode = new Node(); // Prepare a newNode
    newNode -> Value = newValue;
    newNode -> Next = nullptr; // This will be the last node, so next is nullptr
    if(*head == nullptr){
        *head = newNode;    
        return;
    }
    Node* last = *head;
    while(last -> Next != nullptr){
        last = last -> Next; // Find the last node
    }
    last -> Next = newNode; // Insert newNode after the last node(at the end)
}
```
For inserting the call of the function ``insertAtEnd`` would be like this: 
```c++
insertAtEnd(&head, 20); // This will insert a new node with value 20 at the end
```

### 3. Inserting after a given node
To insert a new node **after** a given node in the Linked List, we need to:
1. Check if the given previous node is NULL
2. Prepare a newNode
3. Insert newNode after previous node

![img_insertAfterANode](https://media.geeksforgeeks.org/wp-content/uploads/20240729101116/Insertion-at-a-Specific-Position-of-the-Singly-Linked-List.webp)

How you can implement it in C++:
```c++
void insertAfterNode(Node* prevNode, int newValue){
    if(prevNode == nullptr){
        std::cout << "The given previous node cannot be NULL" << std::endl;
        return;
    }
    Node* newNode = new Node(); // Prepare a newNode
    newNode -> Value = newValue;
    newNode -> Next = prevNode -> Next; // Insert newNode after previous node
    prevNode -> Next = newNode;
}
```
For inserting the call of the function ``insertAfterNode`` would be like this: 
```c++
insertAfterNode(second, -1); // This will insert a new node with value 25 after the second node
```


### Author:
- **Name**: Sergio Real Gonzalvo
- **Email**: sergiete.real@gmail.com