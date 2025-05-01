# EXERCISE 9: Applications of Queue - SJF (Shortest Job First Scheduling)

## DATE:
*13-03-2025*

## AIM:
To incorporate the code to calculate the **Total Waiting Time** and **Average Waiting Time** in **Shortest Job First (SJF)** scheduling algorithm.

---

## Algorithm:
1. Start the program.
2. Input the number of processes.
3. Input the **burst time** for each process.
4. Sort the processes based on **burst time** in ascending order (Shortest Job First).
5. Calculate **waiting time** for each process:
   - Waiting Time of first process = 0
   - Waiting Time of next process = Waiting Time of previous process + Burst Time of previous process
6. Calculate **Total Waiting Time** by summing individual waiting times.
7. Calculate **Average Waiting Time** = Total Waiting Time / Number of Processes.
8. Display the Waiting Times, Total Waiting Time, and Average Waiting Time.
9. End the program.

---

##  Program:
```c
/*
Program to find the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
Developed by: SHAKTHI KUMAR S
RegisterNumber: 212222110043
*/

#include <stdio.h>

// Function to swap two integers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int n, i, j;
    int bt[20], wt[20], total_wt = 0;
    float avg_wt;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    printf("Enter the burst times for each process:\n");
    for (i = 0; i < n; i++) {
        printf("Burst time for Process %d: ", i + 1);
        scanf("%d", &bt[i]);
    }

    // Sorting burst times using simple Bubble Sort
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (bt[j] > bt[j + 1]) {
                swap(&bt[j], &bt[j + 1]);
            }
        }
    }

    // Waiting time for the first process is 0
    wt[0] = 0;

    // Calculating waiting time
    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    printf("\nProcess\tBurst Time\tWaiting Time\n");
    for (i = 0; i < n; i++) {
        printf("%d\t%d\t\t%d\n", i + 1, bt[i], wt[i]);
        total_wt += wt[i];
    }

    avg_wt = (float)total_wt / n;

    printf("\nTotal Waiting Time = %d\n", total_wt);
    printf("Average Waiting Time = %.2f\n", avg_wt);

    return 0;
}
```


## Output:

![image](https://github.com/user-attachments/assets/1f93ad93-8012-42e3-948d-25f6236a70c8)

## Result:
Thus, the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm is implemented successfully.
