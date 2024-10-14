> To calculate the average waiting times for the given processes using both First-Come, First-Served (FCFS) and Shortest Job First (SJF) non-preemptive scheduling algorithms.


Given processes: 

| Process | Arrival Time | Burst Time |
| ------- | ------------ | ---------- |
| P1      | 0.0          | 8          |
| P2      | 0.4          | 4          |
| P3      | 1.0          | 1          |

a) Average waiting time with FCFS scheduling algorithm:

1. P1 starts at 0, finishes at 8 Waiting time for P1 = 0
2. P2 starts at 8, finishes at 12 Waiting time for P2 = 8 - 0.4 = 7.6
3. P3 starts at 12, finishes at 13 Waiting time for P3 = 12 - 1.0 = 11

Average waiting time = (0 + 7.6 + 11) / 3 = 6.2 units

b) Average waiting time with SJF scheduling algorithm:

1. P1 starts at 0, finishes at 8 (only process available at t=0) Waiting time for P1 = 0
2. P3 starts at 8, finishes at 9 (shortest job among P2 and P3) Waiting time for P3 = 8 - 1.0 = 7
3. P2 starts at 9, finishes at 13 Waiting time for P2 = 9 - 0.4 = 8.6

Average waiting time = (0 + 7 + 8.6) / 3 = 5.2 units

Therefore: a) The average waiting time for these processes with the FCFS scheduling algorithm is 6.2 units. b) The average waiting time for these processes with the SJF scheduling algorithm is 5.2 units.

As we can see, in this case, the SJF algorithm results in a lower average waiting time compared to FCFS.