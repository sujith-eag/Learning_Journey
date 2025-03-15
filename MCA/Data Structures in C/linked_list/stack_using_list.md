

```c

#include <stdio.h>
#include <stdlib.h>

struct node 
{
    int data;
    struct node *next;
}*top = NULL;

void push(int e) 
{
    struct node* new = (struct node*)malloc(sizeof(struct node));  // Local variable
    if (new == NULL) 
    {
        printf("Stack is Full\n");
        return;
    }
    new->data = e;
    new->next = top;
    top = new;
    printf("******************************************************\n");
    printf("\nElement %d is Pushed \n", e);
    printf("******************************************************\n");
}

void pop() 
{
    if (top == NULL) 
    {
        printf("******************************************************\n");
        printf("Stack is Under Flow \n");
        printf("******************************************************\n");
    } 
    else 
    {
        struct node* temp = top;
        printf("******************************************************\n");
        printf("Element %d is popped \n", top->data);
        printf("******************************************************\n");
        top = top->next;
        free(temp);
    }
}

void peep() 
{
    if (top == NULL) 
    {
        printf("******************************************************\n");
        printf("Stack is Under Flow \n");
        printf("******************************************************\n");
    } 
    else 
    {
        printf("******************************************************\n");
        printf("The Top Most Element is %d\n", top->data);
        printf("******************************************************\n");
    }
}

void display() 
{
    if (top == NULL) 
    {
        printf("Stack is Empty \n");
    } 
    else 
    {
        struct node* temp = top;
        printf("Elements of Stack are \n");
        printf("******************************************************\n");
        while (temp != NULL) 
        {
            printf("%d \n", temp->data);
            temp = temp->next;
        }
    }
}

int main() {
    int e, ch;
    while (1) {
        printf("\n\n1->Insert element \t2->Delete element \n3->Peep \t\t4->Display \n5->Exit\n");
        printf("\nEnter choice:\n");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter the element to be pushed \n");
                scanf("%d", &e);
                push(e);
                break;
            case 2:
                pop();
                break;
            case 3:
                peep();
                break;
            case 4:
                display();
                break;
            case 5:
                exit(0);
            default:
                printf("Enter the choice Correctly\n");
        }
    }
    return 0;
}
```