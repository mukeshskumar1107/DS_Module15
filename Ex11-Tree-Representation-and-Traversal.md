# Ex11 Tree Representation and Traversal
## DATE: 20-03-2025
## AIM:
To write a C function to perform post order traversal of a binary tree.

## Algorithm
1. Start 
2. Define a function display_postorder() that takes a pointer to the root node of the tree. 
3. Check if the current node (root_node) is not null. 
4. Recursively call display_postorder() for the left child of the current node. 
5. Recursively call display_postorder() for the right child of the current node. 
6. After visiting both children, print the value of the current node. 
7. End 

## Program:
```c
/*
Program to perform post order traversal of a binary tree.
Developed by: MUKESH KUMAR S
Register Number: 212223240099  
*/

/*
struct node
{
    int value;
    struct node *left_child, *right_child;
};
*/

void display_postorder(struct node *root_node)
{
    // write your code here
    if (!root_node)
    {
        return;
    }
    display_postorder(root_node->left_child);
    display_postorder(root_node->right_child);
    printf("%d\n", root_node->value);
}
```

## Output:
<img width="950" height="531" alt="image" src="https://github.com/user-attachments/assets/d9fced92-4401-4f42-a4a0-5008f4781186" />



## Result:
Thus, the function to perform post order traversal of a binary tree is implemented successfully
