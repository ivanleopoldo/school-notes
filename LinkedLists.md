# **Linked Lists**

**Linked Lists** is a linear data structure. Unlike arrays, elements of a linked lists or **nodes**  are not stored at a contiguous location or there are gaps between the nodes and these **nodes are linked using pointers**.

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2013/03/Linkedlist.png">

It is composed of data variables and a self-referenced pointer variable. A basic linked list definition would be:

```c
typedef struct node
{
    int data;
    struct node* next;
} node, *LL; //*LL is a pointer to struct node.
```

---

## **Terms**

<table>
<theader>
    <tr>
        <td><b>Term</b></td>
        <td><b>Definition<b></td>
    </tr>
</theader>
<tbody>
    <tr>
        <td>head</td>
        <td>first node of the list</td>
    </tr>
    <tr>
        <td>dynamic memory allocation</td>
        <td>a memory allocation technique that allows memory to be allocated dynamically</td>
    </tr>
    <tr>
        <td>update statement</td>
        <td>part of the for loop where the increment usually is is</td>
    </tr>
    <tr>
        <td>pass by copy</td>
        <td>pass a copy of the list</td>
    </tr>
    <tr>
        <td>pass by address</td>
        <td>pass the address of the list</td>
    </tr>
</tbody>
</table>

---

## **Usage**

### **Creation**

To create a linked list, we have to dynamically allocate memory to each node.

```c
typedef struct node
{
    int data;
    struct node* next;
} node, *LL;

int main()
{
    LL first = (LL)malloc(sizeof(node));
    LL second = (LL)malloc(sizeof(node));

    first->data = 1;
    first->next = second; //points to the second dynamically allocated memory.

    second->data = 2;
    second->next = NULL; //NULL signifies end of the list.

    return 0;
}
```

### **Pointer To Node Traversal**

This is used to traverse the linked list without changing the contents of the nodes.

The code implementation would be:

```c
LL temp;
for(temp = head; temp != NULL; temp = temp->next)
{
    //do something
    //since it is not node pointer traversal
    //any changes here would not change the linked list.
    //only within the block.
};
```

### **Pointer to Pointer to Node Traversal**

This is used when you want to update, insert, and delete the linked list.

The strategy would be to dereference the temp variable.

The code implementation would be:

```c
LL *temp;
for(temp = head; *temp != NULL; temp = &(*temp)->next)
{
    //do something
}
```

---

## **Functions**

### **Display**

This function is used to display the data of each node in the linked list.

Code using while loop:

```c
void whileLoopDisplay(LL head)
{
    while(head != NULL)
    {
        printf("%d", head->data);
        head = head->next;
    }
}
```

Code using for loop:

```c
void forLoopDisplay(LL head)
{
    for(head; head != NULL; head = head->next)
    {
        printf("%d", head->data);
    }
}
```

### **Insert**

This function is used to insert a node to any index in the linked list.

Insertion at the start code:

```c
void insertStart(LL *head, int data)
{
    LL newnode = (LL) malloc(sizeof(node));

    newnode->data = data;
    newnode->next = *head;

    *head = newnode;
}
```

Insertion at the end code:

```c
void insertEnd(LL *head, int data)
{
    LL newnode = (LL)malloc(sizeof(node));
    LL temp = *head;

    newnode->data = data;
    newnode->next = NULL;

    while(temp->next!=NULL)
    {
        temp = temp->next;
    }

    temp->next=newnode;
}
```

Insert in sorted linked list code:

```c
void insertSorted(LL *head, int data)
{
    LL temp=(LL)malloc(sizeof(node)), *trav;

    for(trav = head; *trav != NULL && (*trav)->data < data; trav = &(*trav)->next){}

    if(temp != NULL)
    {
        temp->data = data;
        temp->next = *trav;
        *trav = temp;
    }
}
```

### **Delete**

This function is used to delete nodes in the linked list.

Deletion first occurrence code:

```c
void delete(LL *head, int data)
{
    LL *temp = *head;
    LL *prev;

    if(temp!=NULL && temp->data == data)
    {
        *head = temp->next;
        free(temp);
        return;
    }

    while(temp!=NULL && temp->data !=data)
    {
        prev = temp;
        temp = temp->next;
    }

    prev->next = temp->next;

    free(temp);
}
```

Delete all occurrences code:

```c
LL deleteAll(LL head, int x)
{
    if (!head)
        return head;
    while (head && head->data == x)
        head = head->next;
    LL curr = head, prev = NULL;
    while (curr) {
        if (curr->data == x)
            prev->next = curr->next;
        else
            prev = curr;
        curr = curr->next;
    }
    return head;
}
```

---

## **Sources**

1. [C program to create and traverse a Linked List](https://codeforwin.org/2015/09/c-program-to-create-and-traverse-singly-linked-list.html)
2. [Linked List Traversal](https://takeuforward.org/data-structure/linked-list-traversal/)
3. [Delete all occurrences of a given key in a linked list](https://www.geeksforgeeks.org/delete-occurrences-given-key-linked-list/)