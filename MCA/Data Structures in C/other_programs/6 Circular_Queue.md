
In a circular queue, the `tail` pointer wraps around to the front when the queue is full, making efficient use of the available space in the array. This avoids the problem of running out of space when elements are dequeued, as would happen in a linear queue.

#### **Basic Logic**

- **Circular Structure**: The queue is implemented using a circular array, so when the `tail` reaches the end of the array, it wraps around to the beginning.
- **Pointers**: 
  - `head` points to the first element (front) of the queue.
  - `tail` points to the next available position for insertion (back).
  - After dequeuing, the `head` is incremented, and after enqueueing, the `tail` is incremented, with both wrapping around if necessary.

#### Key Difference

In enqueue -
Checking for full - `if ( head == (tail + 1) % n )`.
Incrementing tail circularly `tail = (tail + 1) % n;` and adding value to stack at tail.

In dequeue -
if there is only one element in stack `head == tail`, Resetting the head and tail to `-1` 
else, print from head and circularly incrementing the head using `head = (head + 1) % n;`

For display -
Using `int i == head` and `while (i != tail)` to iterate all elements from head to tail (circularly) .  by  incrementing `i` circularly, `i = (i + 1) % n;`       
Handling the last left out element after while loop by printing `stack[head]`


____

#### **Variables**

- **`int n`**: Size of the queue.
- **`int head = -1, tail = -1`**: Initialize `head` and `tail` to `-1` to indicate an empty queue.
- **`queue[n]`**: Array of integers (or relevant type) used to represent the queue.
- **`ele`**: The value to be added to the queue (enqueue operation).
- **`ch`**: Integer variable used to capture the user's choice for queue operations.

#### **Implementation Logic**

1. **Global Variables**: 
   - Declare `n`, `head = -1`, and `tail = -1` globally to manage the circular queue.
   - Functions (`enque`, `deque`, `display`) are declared, all returning `void`.
   
2. **Input Handling**:
   - In `main()`, take the size of the queue (`scanf("%d", &n)`).
   - Declare `queue[n]` to store elements and `ele` to hold the value to be inserted.

3. **Loop for Operations**:
   - A `while(1)` loop continuously displays options and performs the selected operation.
   - User selects an operation, and the corresponding function is executed.

4. **Queue Operations**:
   - **Enqueue**: Adds an element at the `tail` position, checks if the queue is full, and updates the `tail`.
   - **Dequeue**: Removes an element from the front (`head`), and updates the `head`.
   - **Display**: Prints all elements from `head` to `tail`, considering the circular nature of the queue.

#### **Function Logic**

1. **`enque`**: 
   - Checks if the queue is full (`(tail + 1) % n == head`).
   - If not full, increment `tail`, wrap if necessary, and inserts the value at `queue[tail]`.
   - If `head` is `-1` (first insertion), it increments `head` to indicate the queue is no longer empty.
   
2. **`dequ`**:
   - Checks if the queue is empty (`head == -1`).
   - If not empty, removes the element at `head` and increments `head`. The `head` wraps around if needed.
   
3. **`display`**:
   - Checks if the queue is empty (`head == -1`).
   - If not empty, prints elements starting from `head` to `tail`, considering the circular nature.

---



### **Circular Queue Implementation**

```c
#include <stdio.h>
#include <stdlib.h>

int n, head = -1, tail = -1;

void enqu(int queue[], int x);
void dequ(int queue[]);
void display(int queue[]);

void main()
{
    printf("Enter the size of the Queue: \n");
    scanf("%d", &n);
    int queue[n], ele;

    while(1)
    {
        int ch;
        printf("Make a choice:\n");
        printf("\n0.Exit\t1.Enqueue\n2.Dequeue\t3.Display\n");
        scanf("%d", &ch);

        if (ch == 0)
            exit(0);
        else if (ch == 1)
        {
            printf("\nProvide the Number to Add: \n");
            scanf("%d", &ele);
            enqu(queue, ele);
        }
        else if (ch == 2)
            dequ(queue);
        else if (ch == 3)
            display(queue);
        else
            printf("Enter a Proper choice\n");
    }
}

// Function to enqueue (add an element to the circular queue)
void enqu(int queue[], int x)
{
    if (head == ((tail + 1) % n) )  // Check if queue is full
    {
        printf("\nThe Queue is Full\n");
    }
    else
    {
        if (head == -1)  // First element to be added
            head = 0;  // Set head to 0 (indicating the queue is not empty)
        tail = (tail + 1) % n;  // Increment tail (circularly)
        queue[tail] = x;  // Insert element at the tail
        printf("\nNumber %d has been inserted in the Queue\n\n", x);
    }
}

// Function to dequeue (remove an element from the circular queue)
void dequ(int queue[])
{
    if (head == -1)  // Queue is empty
        printf("\nThe Queue is empty\n");
    else
    {
        printf("The Number %d has been removed\n", queue[head]);
        if (head == tail)  // If there's only one element in the queue
        {
            head = tail = -1;  // Reset the queue to empty
        }
        else
        {
            head = (head + 1) % n;  // Increment head (circularly)
        }
    }
}

// Function to display all elements in the circular queue
void display(int queue[])
{
    if (head == -1)  // Queue is empty
        printf("\nThe Queue is empty\n");
    else
    {
        printf("The Elements in the Queue are: \n");
        int i = head;
        while (i != tail)  // Display elements from head to tail (circularly)
        {
            printf("%d \t", queue[i]);
            i = (i + 1) % n;  // Circular increment
        }
        printf("%d \n", queue[tail]);  // Print the last element (tail)
    }
}
```

---

### **Key Points for Circular Queue Implementation**

1. **Circular Behavior**:
   - **Enqueue**: When `tail` reaches the end of the queue (`tail == n-1`), the `tail` pointer wraps around to the front of the queue, allowing reuse of empty spaces.
   - **Dequeue**: After an element is removed, `head` increments circularly. If `head == tail`, the queue is reset to empty (`head = tail = -1`).
   
2. **Full Queue Check**: 
   - The queue is full if `(tail + 1) % n == head`, meaning there is no space left for new elements.

3. **Display Operation**:
   - The `display` function uses a `while` loop to iterate through the queue from `head` to `tail` while considering circular wrapping.

4. **Efficiency**:
   - **Time Complexity**: All operations (`enqueue`, `dequeue`, and `display`) have constant time complexity (`O(1)` for enqueue and dequeue, `O(n)` for display).
   - **Space Complexity**: The queue uses `O(n)` space where `n` is the size of the queue.

Circular queue implementation efficiently handles the queue operations, ensuring that space is utilized effectively and avoiding the issue of "unused space" in a typical linear queue.


```c
#include <stdio.h>
#include <stdlib.h>

int n, head = -1, tail=-1;

void enqueu(int queue[], int x);
void dequeu(int queue[]);
void display(int queue[]);

int main()
{
	printf("Enter the size of queue\n");
	scanf("%d", &n);
	int queue[n], ele;

	while(1)
	{
		int ch;
		printf("Select choises: 0, 1, 2, 3 \n");
		scanf("%d", &ch);
		
		if(ch==0)
			exit(0);
		else if(ch ==1)
		{
			printf("enter the number: \n");
			scanf("%d", &ele);
			enqueu(queue, ele);
		}
		else if (ch == 2)
		{
			dequeu(queue);
		}
		else if (ch == 3)
		{
			display(queue);
		}
	}
}

void enqueu(int queue[], int x)
{
	if (head == ( (tail + 1) % n ))
		printf("Queue is full\n");
	else
	{
		if ( head == -1)
			head = 0;
		tail = (tail + 1) %n;
		queue[tail] = x;
		printf("Number %d has been added at %d", x, tail);
	}
}
void dequeu(int queue[])
{
	if ( head == -1)
		printf("Queue is empty\n");
	else
	{
		printf("element %d has been removed from %d", queue[head], head);
		if( head == tail)
			head = tail = -1;
		else
			head = (head + 1) % n;
	}
}
void display(int queue[])
{
	if (head == -1 )
		printf("The queue is empty\n");
	else
	{
		int i = head;
		while ( i != tail)
		{
			printf("%d \n",queue[i]);
			i = (i+1) % n;
		}
		printf("%d \n", queue[tail]);
	}
}
```


```c
#include <stdio.h>
#define MAX 5

int queue[MAX];
int front = -1, rear = -1;

// Function to insert an element into the queue (enqueue)
void enqueue(int value) 
{
    if ( front == (rear + 1) % MAX) 
    {
        printf("Queue is full! Cannot insert %d\n", value);
    } 
    else 
    {
        if (front == -1) 
        {  // If the queue is empty
            front = 0;
        }
        rear = (rear + 1) % MAX;  // Circular increment of rear
        queue[rear] = value;
        printf("%d inserted into the queue.\n", value);
    }
}

// Function to delete an element from the queue (dequeue)
int dequeue() {
    if (front == -1) 
    {  // If the queue is empty
        printf("Queue is empty! Cannot dequeue.\n");
        return -1;
    } 
    else 
    {
        int value = queue[front];
        if (front == rear) 
        {  // If there is only one element
            front = rear = -1;  // Reset the queue
        } 
        else 
        {
            front = (front + 1) % MAX;  // Circular increment of front
        }
        return value;
    }
}

// Function to display the elements in the queue
void display() {
    if (front == -1) 
    {
        printf("Queue is empty!\n");
    } 
    else 
    {
        printf("Queue elements: ");
        int i = front;
        while (i != rear) 
        {
            printf("%d ", queue[i]);
            i = (i + 1) % MAX;  // Circular increment of index
        }
        printf("%d\n", queue[rear]);  // Print the last element
    }
}

// Main function to demonstrate the queue operations
int main() {
    enqueue(10);  // Insert 10
    enqueue(20);  // Insert 20
    enqueue(30);  // Insert 30
    enqueue(40);  // Insert 40
    enqueue(50);  // Insert 50
    enqueue(60);  // This will fail because the queue is full
    
    display();    // Display queue
    
    printf("%d dequeued from the queue.\n", dequeue());  // Remove 10
    display();    // Display queue after dequeue
    
    enqueue(60);  // Insert 60 after dequeue
    display();    // Display queue after enqueue

    return 0;
}
```