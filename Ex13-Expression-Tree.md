# Ex13 Expression Tree
## DATE: 20-03-2025
## AIM:
To write a C function to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.

## Algorithm
1. Start 
2. Print node data in preorder then traverse left then right 
3. Traverse left in inorder then print node data then traverse right 
4. Traverse left in postorder then traverse right then print node data 
5. Recursive approach is used for all three traversal methods 
6. Functions handle each tree node using tree->d, tree->l, tree->r 
7. End    

## Program:
```c
/*
Program to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.
Developed by: MUKESH KUMAR S
Register Number: 212223240099 
*/

#include <stdio.h>
#include <stdlib.h>
struct n
{
    char d;
    struct n *l;
    struct n *r;
};
char pf[50];
int top = -1;
struct n *a[50];
int r(char inputch)
{
    if (inputch == '+' || inputch == '-' || inputch == '*' || inputch == '/')
        return (-1);
    else if (inputch >= 'A' || inputch <= 'Z')
        return (1);
    else if (inputch >= 'a' || inputch <= 'z')
        return (1);
    else
        return (-100);
}
void push(struct n *tree)
{
    top++;
    a[top] = tree;
}
struct n *pop()
{
    top--;
    return (a[top + 1]);
}
void construct_expression_tree(char *suffix)
{
    char s;
    struct n *newl, *p1, *p2;
    int flag;
    s = suffix[0];
    for (int i = 1; s != 0; i++)
    {
        flag = r(s);
        if (flag == 1)
        {
            newl = (struct n *)malloc(1 * sizeof(struct n));

            newl->d = s;
            newl->l = NULL;
            newl->r = NULL;
            push(newl);
        }
        else
        {
            p1 = pop();
            p2 = pop();
            newl = (struct n *)malloc(1 * sizeof(struct n));
            newl->d = s;
            newl->l = p2;
            newl->r = p1;
            push(newl);
        }
        s = suffix[i];
    }
}
void preOrder(struct n *tree)
{
    // type your code here
    if (!tree)
    {
        return;
    }
    printf("%c", tree->d);
    preOrder(tree->l);
    preOrder(tree->r);
}
void inOrder(struct n *tree)
{
    // type your code here
    if (!tree)
    {
        return;
    }
    inOrder(tree->l);
    printf("%c", tree->d);
    inOrder(tree->r);
}
void postOrder(struct n *tree)
{
    // type your code here
    if (!tree)
    {
        return;
    }
    postOrder(tree->l);
    postOrder(tree->r);
    printf("%c", tree->d);
}
int main()
{

    scanf("%s", pf);
    construct_expression_tree(pf);
    // printf("\nIn-Order Traversal : ");
    inOrder(a[0]);
    printf("\n");
    // printf("\nPre-Order Traversal : ");
    preOrder(a[0]);
    printf("\n");
    // printf("\nPost-Order Traversal : ");
    postOrder(a[0]);
    printf("\n");
    return 0;
}
```

## Output:
<img width="403" height="286" alt="image" src="https://github.com/user-attachments/assets/73d3bd92-b157-42c2-a582-a9c1bd3fad39" />



## Result:
Thus, the C program to display the Expression Tree in the format of In-order ,Pre-order and Post-order traversal.
