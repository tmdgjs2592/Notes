# Week 1
****
Application Binary Interfaces
Application Programming Interfaces
Proprietary vs Open Standards
Evolution for technology and applications
****
# Week 2 Processes, Execution, and State
****
**Ch 4 Abstraction**
Virtualizing: making an illusion that multiple CPUs exist by running multiple processses

Machine state
- memory
- registers

Eager/Lazy loading process: OS eagerly loads data all at once before running the program or lazily loads as the need be.

Heap: dynamically allocated storage
stack: local variables, function parameters, and return addresses

Process, address space, Program counter, stack pointer, process API, process states, process list, process control block
****
**Chapter 5** **Process API**

**fork()**
- the process that is created by fork() is an exact copy of the calling process.
- the child gets its own copy of the address space, registers, PC.
$\rightarrow$ non-deterministic

**wait()**
- a parent may wait for child to finish by using wait() $\rightarrow$ deterministic

**exec()**
- when you want to run a program that is different from the calling program.

Keyword: fork, wait, exec, input/output redirection, pipes, superuser 
****
**Chapter 6 Limited Direct Execution**

Limited Direct Execution

trap, return-from-trap, trap table
- trap to execute a system call, jumps into the kernel
	- from privilege level to kernel mode


**cooperative and noncoopeartive approach for OS regaining control** 
- cooperative: OS regains the control through system calls
- noncooperative: OS regains the control through the interrupt timer.
	- timer goes off and OS regains the control

keyword: system-call number, a cooperative approach, timer interrupt, interrupt handler, non-cooperative approach, context switch
****
Object Modules, Linkage Editing, Libraries
Compiler, Assembler, Linkage editor, Program loader
Static vs Shared Libraries, Dynamically Loaded Libraries
Implicitly/Explicitly Loaded Dynamically Loadable Libraries
Stack Frames and Linkage Conventions
****
# Week 3

**Chapter 7**

-Turnaround time: time at which the job completes minus the time at which the job arrived in the system

-Metric of interest: fairness - measured by Jain’s Fairness Index

FIFO - First In First Out/First Come First Serve

-A, B, C all arrive at the same time and it takes 10 ms each

-Turnaround time = (10 + 20 + 30)/3 = 20 ms

-However, now A is 100 ms

-Turnaround time is now 110 ms

-Convoy effect: relatively short potential consumers of a resource get queued behind a heavyweight resource consumer

SJF - Shortest Job First
- Runs the shortest job first
- A runs for 100 ms, B and C for 10 ms

-SJF performs better for average turnaround time from 110 ms to 50 ms

- (10+20+120)/3 = 50

-This time, A arrives at t=0 and for 100 seconds, B and C arrive at t=10 and need to run for 10 seconds each

-Average turnaround time is 103.33 seconds

-Suffers from convoy effect still

—---------------------------------------------------------------------------

STCF - Shortest Time to Completion First

-Any time a new job enters the system, determines which of the remaining jobs has the least amount of time left, then schedules it

-Same scenario as the one in SJF

-STCF would preempt A and run B and C to completion. When B and C finish, A finishes

-Much improved average turnaround time ((120-0) + (20-10) + (30-10))/3 = 50 sec

—---------------------------------------------------------------------------

New metric: Response time

Response time is the time from when the job arrives in a system to the first time it is scheduled

—---------------------------------------------------------------------------

RR - Round Robin

-RR runs a job for a time slice (scheduling quantum) and switches to the next job in the run queue

-3 jobs (A,B,C) all arrive at the same time and run for 5 seconds each

-Average response time: (0+1+2)/3 = 1

-SJF would be (0+5+10)/3 = 5

-RR optimizes response time but is bad for turnaround

-The others (SJF, STCF) optimize turnaround

—--------------------------------------------------------------------------

  

**Chapter 7**

—----------------------------------------------------------------------------

Multi-Level Feedback Queue

  

**Definition:**

- A scheduling algorithm that allows a process to move between different priority queues.

- Designed to improve the responsiveness of interactive systems and optimize CPU utilization.

  

**Key Characteristics:**

- **Multiple Queues:** Contains multiple queues, each with a different priority level.

- **Dynamic Priority Adjustment:** Processes can move between queues based on their behavior and execution history.

- **Aging:** Prevents starvation by gradually increasing the priority of long-waiting processes.

  

**How it Works:**

1. **Initialization:**

   - Processes start in the highest-priority queue.

   - Each queue has its own scheduling algorithm (often Round Robin).

  

2. **Execution:**

   - The scheduler selects processes from the highest-priority non-empty queue.

   - If a process uses up its time slice without finishing, it is moved to a lower-priority queue.

  

3. **Priority Adjustment:**

   - **Promotions:** Processes can be moved to a higher-priority queue if they exhibit certain behaviors, such as waiting for I/O.

   - **Demotions:** Processes that use their entire time slice are moved to a lower-priority queue.

  

4. **Time Quantum:**

   - Higher-priority queues have shorter time quanta to ensure quick responsiveness for interactive processes.

   - Lower-priority queues have longer time quanta to allow CPU-bound processes to run efficiently.

  

5. **Starvation Prevention:**

   - To avoid starvation of lower-priority processes, the MLFQ uses aging, which gradually increases the priority of processes that wait in the system for a long time.

  

**Advantages:**

- **Flexibility:** Adapts to a variety of process behaviors.

- **Responsiveness:** Prioritizes interactive processes, improving system responsiveness.

- **Efficient CPU Utilization:** Balances the load between CPU-bound and I/O-bound processes.

  

**Disadvantages:**

- **Complexity:** More complex to implement and manage compared to simpler scheduling algorithms.

- **Overhead:** Managing multiple queues and moving processes between them introduces additional overhead.

  

**Examples of Usage:**

- Common in interactive and real-time systems where different types of processes coexist and require different scheduling strategies.

—-----------------------------------------------------------------------------------

  

**Chapter 13**

Address Spaces

Terms: multiprogramming, utilization, efficiency, time sharing, protection, easy to use, address space, code, stack, heap, threads, abstraction, 

Goals of VM: transparency, efficiency, protection

Protection enables us to deliver the property of isolation

  

**Chapter 14**

Two types of memory: stack (automatic) and heap (explicit allocations and deallocations)

Not allocating enough memory can result in a buffer overflow - occurs when the amount of data in the buffer exceeds its storage capacity

Memory leaks occur when you forget to free memory

Dangling pointer can crash the program or overwrite valid memory (e.g. you call free() then malloc() again to allocate something else, which then recycles the errantly freed memory

  

**Chapter 15**

Address Translation

-Use base and bounds that is also referred as dynamic relocation

-two hardware registers within each CPU, one base and one bounds register

-Each memory reference generated by the process is a virtual address

-The hardware in turn adds the contents of the base register to this address and the result is a physical address that can be issued to the memory system

-Transforming a virtual address into a physical address is a technique called address translation

-Part of the processor that helps with address translation is called the memory management unit

  

**Chapter 16**

Segmentation

-Large amount of unused address space is called sparse address space

-Segmentation fault or violation arises from a memory access on segmented machine to an illegal address

-Protection bits add basic support that adds a few bits per segment indicating whether or not a program can be read or write a segment

We can think of segmentation as coarse grained, as it chops up the address space into relatively large, coarse chunks

-Or there can be large number of smaller segments, referred to as fine-grained segmentation

  

**Chapter 17**

Free-space management

-Combines the adjacent free space in the list instead of having separate ones: coaslescing

-BEST FIT (smallest fit): First search through the free list and find chunks of free memory >= requested size

-Return the smallest in the group of candidates

-Best fit tries to reduce wasted space

-

-WORST FIT: Opposite of best fit, find the largest chunk and return the requested amount

- Tries to leave big chunks free instead of lots of small chunks that can arise from a best-fit approach

-approach can be costly

-Excess fragmentation while still having high overheads

  

FIRST FIT: Find the first block that is big enough and returns the request amount to the user

-Has the advantage of speed, no exhaustive search of all the free spaces

-sometimes pollutes the beginning of the free list with small objects

-Address based ordering keeps the list ordered by the address of the free space. Coalescing becomes easier, and fragmentation tends to be reduced

  

NEXT FIT: Keeps an extra pointer to the location within the list where one was looking last

-Idea is to spread the searches for free space throughout the list more uniformly, thus avoiding splintering of the beginning of the list

  

Binary buddy calculator

**

# Week 4
****
**Chapter 18 Paging**
Segmentation, Fragmented, Paging, protection bits, present bit, dirty bit, reference bit
****
**Chapter 19 Faster Translations (TLBs)**
TLB: Translation-lookaside buffer (hardware cache)
MMU: memory-management unit
Temporal locality, Spatial locality
fully-associative: any given translation can be anywhere in the TLB, and that the hardware will search the entier TLB in parallel to find the desired translation.
protection, dirty, valid bits
cache replacement --> LRU
****
**Chapter 21 Beyond Physical Memory: Mechanisms**
Hard disk drive
swap space: space reserved on the disk for moving pages back and forth.
Page Table Entry (PTE)
Process of memory reference:
- Checks TLB first
	- if hit, produce a resulting physical address and fetch from memory
	- if not hit, get the page table entry from the page table
	- if the page is valid and present in physical memory, get PFN and load it in the TLB.
Page fault: act of accessing a page that is not in physical memory
hardware managed TLB
Software managed TLB
OS is put in charge to handle the page fault
High watermark and low watermark
****
**Chapter 22 Beyond Physical Memory: Policies**

Average Memory Access Time (AMAT): Average memory accessing time + miss rate * average disk accessing time

**Three C's**
- Compulsory miss: misses that result from the emptiness of a cache
- Capacity miss: misses that occur from full capacity
- Conflict miss: misses that occur because of limits on where an item can be placed in a hardware cache.

FIFO (first-in, first-out): pages were simply placed in a queue when they enter the system; when a replacement occurs, the page on the tail of the queue (the “first-in” page) is evicted.

Random: picks a random page to replace under memory pressure.

Workload: dynamically assigning number of pages 

Clock algorithm: Approximating LRU
- LRU is too expensive

Dirty pages

Demand paging: the OS brings the page into memory when it is accessed.

Thrashing: constant state of paging, causing a significant slowdown in system performance. Happens when the system spends more time swapping pages in and out of memroy than executing actual processes.
****
Working sets, page stealing
****
# Chapter 28 (locks)

Spin-lock suffers performance with a single core CPU. If a thread that holds the lock gets preempted by the scheduler, the rest of the threads will waste their entire time slice as they cannot acquire the lock.

Spin-lock works reasonably well with multi-core CPUS, as the thread holding the lock will finish the critical section quicker.

test-and-set: 

park(): putting a calling thread to sleep
unpark(): waking a thread

Lock with queues:
$\rightarrow$ guard is a lock to the if statements so threads can properly either obtain the lock or put themselves on the queue.
$\rightarrow$ if there are threads on the queue still, then don't change the flag because the next thread in the queue will get the lock. because once they are awake, they will be past the lock, meaning they obtain the lock.

futex_wait(address, expected): puts the calling thread to sleep. if it's not equal, the call returns immediately.

futex_wake(address) wakes on thread that is waiting on the queue.
****
# Chapter 30

Condition variable: a queue that threads can put themselves on when a certain condition is not met.

pthread_cond_t c;

If we don't lock it while signal() or wait(), the thread might get interrupted and cause problems. (atomicity)

while loop >>> if 
$\rightarrow$ there are cases where rechecking is required but if statement does not recheck.

producer threads: threads that put data onto the buffer.
consumer threads: threads that consume the data from the buffer.

The problem with one condition variable (with one producer and two consumers)
$\rightarrow$ Say, two consumers run first, in which case both of them would go to sleep. producer runs, fills the buffer, and wakes one of the consumers. Producer tries to fill the buffer again but the buffer has been filled and puts itself to sleep (yield). a consumer wakes, takes the data from the buffer, and signals one of the sleeping threads. If a producer is awake, no problem. If the other consumer is awake, it will see that the buffer is empty and put itself to sleep. Then, all three threads are sleeping.

pthread_cond_broadcast(): wakes up all waiting threads.
****
# Chapter 29 Lock-base Concurrent Data Structures
****
# Chapter 31 

Philosopher at dining table question 
5 philosophers sitting around the table and forks are placed between each philosopher -- thus 5. a philosopher has time to think and time to eat. However, when eating, they have to use both forks on left and right hands. If we were to make a concurrent program of this situation, it would be to think and grab left fork and right fork and eat. However, if all threads grab the left one first, there would be a deadlock -- no one would be able to eat and just wait forever for someone to release the fork. Solution to this would be to change the order of grabbing the fork for one person, say the 5th philosopher grabs the right fork first before the left.
****
# Week 6

**Chapter 32 Common Concurrency Problems**

Atomicity violation: a code region is intended to be atomic, but the atomicity is not enforced during execution. (context switch)
$\rightarrow$ lock

Order violation: Certain order at which threads should be executed exists but it's not enforced. (Thread B runs before Thread A)
$\rightarrow$ condition variable

Deadlock: Each thread is waiting for the other and neither can run.

lock ordering to avoid deadlock: acquire locks in either high-to-low or low-to-high address order.

pthread_mutex_trylock(): grabs the lock and returns success or returns an error code indicating the lock is held.
$\rightarrow$ can cause livelock.
****
**Chapter 36 I/O Devices**

programmed I/O: when the main CPU is involved with the data movement.

Polling: OS asking for the status 
- Can introduce overhead as CPU just spins while polling.
- overhead can be resolved with interrupts, which allows overlap
- OS runs diff process while disk finishes the calling process' request and interrupt when finished to get back on the original process.

Interrupts are only good for slow devices

Direct Memory Access (DMA): device that allows the data transfer between devices and main memory without CPU intervention
- we can use the CPU more efficiently.

Block devices
- request method to enqueue asynchronous DMA requests.
****
# Week 7

**Chapter 39 FIles and Directories**

strace: trace every system call made by a program while it runs.

open file table: each entry in the table tracks which file the descriptor refers to.

fsync(int fd): forces all dirty data to disk. (ensuring all write requests are satisfied)

You can only update a directory indirectly by creating files or another directory within it.
an empty directory has two entries: one entry that refers to itself and other entry refers to its parent.

Symbolic links
ln -s file file2
- formed by holding the pathname of the linked-to file as the data of the link file.
- If the og file is removed, the link will now point to a name that no longer exists.

**Chapter 40 File System Implementation**

Two key aspects for a file system: data structures and access methods

indirect pointers: pointers that point to a block that has more pointers, each of which point to user data.

multi-level index approach: double indirect pointers, triple ,,,

Situation: twelve direct pointers, single and a double indirect block
(4KB blocks, 4 byte pointers)
- twelve direct pointers, each point to 4KB block $\rightarrow$ 12 $\cdot$ 4KB
- single indirect block points to a block that has pointers
	- 4KB/4 byte = 1024 pointers $\rightarrow$ 1024 $\cdot$ 4KB
- double indirect block points to a block that points to another block that has pointers
	- $\rightarrow$ $1024^2$ $\cdot$ 4KB
- Total = (12+1024+$1024^2$) $\cdot$ 4KB

**File Types and Attributes**

Inter-Process Communications Ports (pipe): not a container in which data is stored, more like a channel through which data passes.

meta-data: data that describes data

**An Introduction to DOS FAT Volume and File Structure**

BIOS: Basic I/O Subsystem

DOS: Disk Operating System
FAT: File Allocation Table

bootstrap: code to be loaded into memory and executed when the computer is powered on.
volume descriptors: information describing the size, type, and layout of the <u>filesystem</u> and how to find the other key meta-data descriptors
file descriptors: information that describes a file and points where the actual data is stored on the disk.
free space descriptors: lists of free blocks
file name descriptors: data structures that user-chosen names with each file

File Allocation Table(FAT) is used both as a free list, and to keep track of which blocks have been allocated to which files.

boot block (block 0) contains:
- branch instruction (to the start of the real bootstrap code)
- volume description (BIOS Parameter Block)
- bootstrap code
- optional disk partitioning table
- signature (for error checking)

BIOS Parameter Block contains:
- number of byters per sector
- number of sectors per track
- number of tracks per cylinder
- total number of sectors on the volume
- number of sectors per cluster
- the number of reserved sectors
- the number of Alternate File Allocation Tables
- the number of entries in the root directory

FAT
- free block is indicated by 0.
- If the block is allocated to a file, FAT entry gives the number of the next logical block in the file.
- If such block is the end of a file, it returns -1.

8-bit FAT
- each entry in the FAT is 8 bit $\rightarrow$ $2^8 = 256$
- each entry corresponds to a cluster $\rightarrow$ 256 clusters
- typical cluster size $\rightarrow$ 512 bytes
- max disk size $\rightarrow$ $256 \cdot 512 = 128$ KB


