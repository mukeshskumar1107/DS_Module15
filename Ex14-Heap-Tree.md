# Ex14 Heap Tree
## DATE: 20-08-2025
## AIM:
To write a C function to delete an element in a Heap Tree.

## Algorithm
1. Start 
2. Find the index of the element num in the array. 
3. Swap the element to be deleted with the last element in the array. 
4. Decrease the array size (size) by 1. 
5. Start heapifying from the last non-leaf node (index size/2 - 1). 
6. Call heapify() to restore the heap property for each node. 
7. End   

## Program:
```c
/*
Program to delete an element in a Heap Tree
Developed by: MUKESH KUMAR S
Register Number: 212223240099 
*/

#include <stdio.h>
int size = 0;
void swap(int *a, int *b)
{
    int temp = *b;
    *b = *a;
    *a = temp;
}
void heapify(int array[], int size, int i)
{
    if (size == 1)
    {
        printf("Single element in the heap");
    }
    else
    {
        int largest = i;
        int l = 2 * i + 1;
        int r = 2 * i + 2;
        if (l < size && array[l] > array[largest])
            largest = l;
        if (r < size && array[r] > array[largest])
            largest = r;
        if (largest != i)
        {
            swap(&array[i], &array[largest]);
            heapify(array, size, largest);
        }
    }
}
void insert(int array[], int newNum)
{
    if (size == 0)
    {
        array[0] = newNum;
        size += 1;
    }
    else
    {
        array[size] = newNum;
        size += 1;
        for (int i = size / 2 - 1; i >= 0; i--)
        {
            heapify(array, size, i);
        }
    }
}
void deleteRoot(int array[], int num)
{
    // type your code here
    int i;
    for (i = 0; i < size; i++)
    {
        if (num == array[i])
            break;
    }
    swap(&array[i], &array[size - 1]);
    size -= 1;
    for (int i = size / 2 - 1; i >= 0; i--)
    {
        heapify(array, size, i);
    }
}
void printArray(int array[], int size)
{
    for (int i = 0; i < size; ++i)
        printf("%d ", array[i]);
    printf("\n");
}
int main()
{
    int array[10], n, data, x;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        scanf("%d", &data);
        insert(array, data);
    }

    // printf("Max-Heap array: ");
    // printArray(array, size);
    scanf("%d", &x);

    deleteRoot(array, x);

    printf("After deleting an element: ");

    printArray(array, size);
}
```

## Output:
<img width="1092" height="256" alt="image" src="https://github.com/user-attachments/assets/67ad8015-1099-44b2-8c91-b2bb52a10e4b" />


## Result:
Thus, the function to delete an element in a Heap Tree is implemented successfully.
