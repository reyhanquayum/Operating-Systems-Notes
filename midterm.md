# Topics we Covered
* spend time thinking bout topics covevred in class, labs, readings, HW

## Processes (& calling convention)
* What is a process
    * Process Control Block
* How Processes are Created
    * fork where does process id where is it returning what is 0
* Registers
    * what they are
    *Caller Saved vs Calee Saved
        * registers are fastest things we have access to
        * caller saved register cheaper to use, for temporary values
    * base pointer rbp and rsp
* The Stack
    * *Grows Down*
        * things on bottom are pushed **after** things on top
    * Pushq arg
    ```
    %rsp = %rsp - 8
    (%rsp) = arg
    ```
    * popq
## Calling a Function
* Passing arguments (Convention)
* The call Instruction 
    * eg. does ``pushq`` then transfers control to the argument 
* THe function Prolog
    * sets up stack frame
        *part of stack where function operates
        ``%rbp`` : base pointer
    * know where the return address lives (what)
* Local Variables: Where they live

## Returning from a function
* The function Epilog
    * destroys stack frame - restores callers stack frame
    * calle saved registers
* return value ``%rax`` and ``ret`` pops return adress
* user & kernel mode. 
* traps 
    * syscall like read or open a file
    * exceptions - you did something wrong eg access wrong virtual memory
    * return control back to scheduler 

## Concurrency
* threads
    * differences from proccesses:
        * shared memory vs not shared memory
* mechanisms to control concurrency
    * mutexes
    * condition variables
    * semaphores
    * spin locks
* monitors & how to use them
* deadlock
    * lock ordering method, release and acquire locks in same order
* fairness, starvation & other concerns
    * know what is starvation
    * make no assumption about order locks are acquired ( same for cond vars)
        * who gets notified is random

## Scheduling
 * will not show in midterm, maybe final
 * init ---> runnable --> running -x-x-> blocked(maybe) --> terminated
    * blocking call

## preemptive vs non pre-emptive scheduling
* preemtpive - set an alarm - thread cant run for too long you seize back control every quanta (max length of time to run for)
* non preemptive - the scheduler gets back control when yield is called or you make a blocking call
    * blocking - sometimes you block a process because some condition hasn't been met

* metrics 
    * turnaround time (how long when job submitted until done)
    * output time (how long when input in until output out)
    * system throughput
    * resource utilization (look at disk usage)
    * fairness (everyone has roughly equal time)
* policies
    * FCFS/FIFO - arrival policy
    * STCF - shortest time to completion first (need to know how lon ga task runs for, this is impossible sometimes)
    * round robin, run for a quanta, then for another quanta and so forth
* priorities
    * why useful
    * strict priority - run strictest priority first - can lead ot starvation
    * MLFQ - multilevel feedback queue, anyone who hasn't run for a while I boost them (bubble up) (way to prevent starvation) 
* Lottery / CFS
    * just high level idea
    * way to achieve fairness

## Therac-25
* understand it at a high level
* problem that happened on concurrency

## Virtual Memory
* should know what the point of virtual memory is
* have a finite amt of physical memory - wantn to do 2 things
    * want each process to have a view as if they have access to all their own private memory (isolation)
    * in splittign it up, I don't want program to adopt a weird address layout (therefore it doesn't matter the address layout of original)
    * useful to make it appear that you have more memory available than is present
* movq with an address in it (that address is **virtual**)
