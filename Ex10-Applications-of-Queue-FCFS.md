# EXERCISE 10: Applications of Queue – FCFS (First Come First Serve Scheduling)

## DATE:
*14-03-2025*

## AIM:
To write a C function to **calculate the turnaround time** of each process given their **burst time** and **waiting time** in **First Come First Serve** scheduling algorithm.

---

##  Algorithm:
1. Start the program.
2. Input the number of processes.
3. Input the **burst time** for each process.
4. Calculate the **waiting time** for each process:
   - Waiting time of first process = 0
   - Waiting time of next process = waiting time of previous process + burst time of previous process
5. Calculate the **turnaround time**:
   - Turnaround Time = Burst Time + Waiting Time
6. Display Burst Time, Waiting Time, Turnaround Time for each process.
7. End the program.

---

##  Program:
```c
/*
Program to calculate the turnaround time of each process in FCFS scheduling
Developed by: SHAKTHI KUMAR S
RegisterNumber: 212222110043
*/

#include <stdio.h>

int main() {
    int n, i;
    int bt[20], wt[20], tat[20];
    int total_wt = 0, total_tat = 0;
    float avg_wt, avg_tat;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    printf("Enter burst times for each process:\n");
    for (i = 0; i < n; i++) {
        printf("Burst time for Process %d: ", i + 1);
        scanf("%d", &bt[i]);
    }

    // Waiting time for first process is 0
    wt[0] = 0;

    // Calculating waiting times
    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    // Calculating turnaround times
    for (i = 0; i < n; i++) {
        tat[i] = bt[i] + wt[i];
        total_wt += wt[i];
        total_tat += tat[i];
    }

    avg_wt = (float)total_wt / n;
    avg_tat = (float)total_tat / n;

    printf("\nProcess\tBurst Time\tWaiting Time\tTurnaround Time\n");
    for (i = 0; i < n; i++) {
        printf("%d\t%d\t\t%d\t\t%d\n", i + 1, bt[i], wt[i], tat[i]);
    }

    printf("\nTotal Waiting Time = %d", total_wt);
    printf("\nAverage Waiting Time = %.2f", avg_wt);
    printf("\nTotal Turnaround Time = %d", total_tat);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat);

    return 0;
}
```
## Output:

![image](https://github.com/user-attachments/assets/14c405c0-ce1e-4e21-b7e1-c65086126cc6)



## Result:
Thus, the C function to calculate the turnaround time of each process given their burst time and waiting time in First Come first Serve scheduling algorithm is implemented successfully.
