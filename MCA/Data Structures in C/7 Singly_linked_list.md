

A `node` data type defined using `struct`, containing `int` type for data, and a pointer element `next` of `struct node` data type to hold the location of next `node`.

Creating three more pointers of the same data type `struct node` for operations.
`*new` to hold the location of the newly created `node` from malloc.
`*temp` to hold and link the old `node` pointer to the `new` node address.
`*head` to hold the value of the first node only, used in iteration only (never incremented).
All are assigned value `NULL` to help in first insertion.

A Function to create a new node

Allocating memory for the node using `malloc()` with the size of the `struct node` data structure passed, 
`malloc` return the `void*` pointer, it is typecasted into `(stuct node*)` type and assigned to the new pointer. `new = (struct node*) malloc( sizeof(struct node) ); `

Typecasting the `void*` to a `struct node*`, meaning that the pointer `new` will now point to memory that is created for `struct node`.

The values inside the new node are accessed by dot `.` or arrow `->` method.
`new->data` is assigned whatever user entered.
`new->next` is assigned `NULL` since no nodes exist before it.

Now to pass the address of the new node to the old node.
In first addition, `head` and `temp` will both be `NULL`.
It is checked `head == NULL` and if true then both `head` and `temp` are assigned the value of `new`. Will become the first insertion. No pointers to update inside the `node`

If it is not the first insertion,
`temp` hold the address of the previous node, so the `new` node address is passed to the previous node using `temp`.  `temp->next = new;`
Then the `temp` is given the address of the `new` node to hold it for the next update.


In the display function,
Making a pointer inside the function to be used to traverse the linked list.
`struct node te*;` and assigned the value of the head. `te = head`

The check is done to see if the `head` is `NULL` to make sure there are nodes to traverse.
 `te == NULL` 

else condition will run a while loop by moving the pointer back till the value becomes `NULL` 
`while ( te != NULL)` display the data in the node `te->data`.
Then update `te` to point to the next address stored in the node `te = te->next` 


```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
	int data;
	struct node *next;
}*new=NULL, *head=NULL, *temp=NULL;
void Create(int a)
{
	//struct node *temp;
	new = (struct node*) malloc(sizeof(struct node));
	new->data = a;
	new->next = NULL;
	
	printf("%d \n", new->data);
	printf("%d \n", new->next);
	
	if(head == NULL)
	{
		head = new;
		temp = new;
	}
	else
	{
		temp->next = new;
		temp = new;
	}
	
}

void Display()
{
	struct node *te;
	te=head;
	if(te ==NULL)
	{
		printf("Currently list is empty\n");
		printf("***************************\n");
	}
	else
	{
		while(te !=NULL)
		{
			printf("%d-->",te->data);
			te=te->next;
		}
		printf("\n\n");
	}
}

	
void main()
{
	int a;
	
	while(1)
	{
		int ch;
		printf("\n1.Creating Linked List\n");
		printf("2.Display\n");
		printf("\nEnter choice: ");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:
				printf("Enter the element to be inserted \n");
				scanf("%d", &a);
				Create(a);
				break;
			case 2:
				Display();
				break;
		
			default: printf("Enter the choice Correctly");
			break;
		}
	}	
}
```