# Lecture 9 10/3/2023 - Scheduling

## Process / Thread state - PCB ~ TCB (thread control block)

* scheduler switches to another thread

## Preemtpion:
* preemtpive scheduling:
    * assumption that you will get back the process eventally, there is a max time before getting process back
* cooperative scheduling:
    * there is no timer/bound to the process 

## Scheduling Algorithm/Disciplines

* has a simple goal, lok at set of all runnable threads/processes
    * pick who gets a particular process/thread next

* ask the question: how fast does a program appear to run (turnaround time/ completion time/ response time)

* output time: how long til i start VScode until i end VScode (not scheduling decision)

* turnaround time: for videos and **whatnot**

* **FCFS (First Come First Serve)**
    * run P1 (process 1) until end, then P2, then P3.
    * run until process finishes

* **SJF - Shortest Job First** or **Shortest Time to Completion First - STCF**
    * **Shortest Job First** (non-preemptive)
        * all information has to be present before job
        * P3 (2 sec)
        * P2 (4 sec)
        * P1 (24 sec)
    * **Shortest Time to Completion First** (preemptive)

| Process | Arrival | Time to Completion |
|---|---|---|


### Round Robin

* preemptive:
* **Quanta/Time Slice** - how long a process gets to run
* go to next process 

|Process|Arrival|Time to Completion|
|--|--|--|
|P1|0|24|
|P2| 0| 6|

### Adding back I/O
* how efficient is the system, how many resources are being used (doesn't look at time)

* A: only CPU (1 week of runing)
* B: only CPU (1 week of running)
* C: run forever (1 ms CPU runtime, then block thrn 10ms Disk then unblock)


