#  EXERCISE 6: Dequeue Elements from Circular Queue

## DATE:
*07-03-2025*

##  AIM:
To write a C program to **delete three elements** from a **filled circular queue**.

---

## Algorithm:
1. Start the program.
2. Initialize a circular queue with:
   - `front`, `rear`, and a fixed-size array.
3. Fill the circular queue with elements using **enqueue** operation.
4. Define the **dequeue** function:
   - Check if the queue is empty.
   - If not, remove the element from `front`, and update `front` using circular logic.
5. Perform **three dequeue operations**.
6. Print the updated queue after each deletion.
7. End the program.

---

## Program:
```c
/*
Program to delete three elements from the filled circular queue
Developed by: SHAKTHI KUMAR S
RegisterNumber: 212222110043
*/

#include <stdio.h>
#define SIZE 5

int queue[SIZE];
int front = -1, rear = -1;

// Enqueue function
void enqueue(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Queue is full\n");
        return;
    }
    if (front == -1) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    queue[rear] = value;
}

// Dequeue function
void dequeue() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    printf("Deleted element: %d\n", queue[front]);

    if (front == rear) {
        front = rear = -1; // Queue becomes empty
    } else {
        front = (front + 1) % SIZE;
    }
}

// Display function
void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    printf("Current Queue: ");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    // Filling the circular queue
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50);

    printf("Initial Queue:\n");
    display();

    // Dequeue 3 elements
    printf("\nDeleting 3 elements...\n");
    dequeue();
    display();
    dequeue();
    display();
    dequeue();
    display();

    return 0;
}
```

## Output:

![image](https://github.com/user-attachments/assets/7b8b30fd-baca-4313-bd82-c387dc31b282)


## Result:
Thus, the C program to delete three elements from the filled circular queue is implemented successfully.
