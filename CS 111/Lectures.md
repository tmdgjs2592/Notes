****
# Lecture 1

OS fits between Application Binary Interface and Hardware.
Only OS can access previleged instruction set.
Instructions in Privileged Instruction Set
- Accessing memory (reading/writing)
- loading values to registers
****
# Lecture 3

while the process is running, the code is static 
Process is not shared 
Local variables are kept in stack frame
Global variables are kept in the data area
****
# Lecture 4

You want execute OS code as little as possible (Limited Direct Execution)
****
# Lecture 5

Costs of a Context Switch
- Losing instruction and data caches, slowing down the next hundred instructions
****
# Lecture 6
****
# Lecture 7
**Use processes**
- When there are limited interactions and shared resources
- running separate programs
- programs with distinct privileges
- to firewall the program crash
	- If a process fails, it doesn't take the rest with it, whereas if a thread fails, the rest of threads might crash.

**Use threads**
- Parallel in a single program
- frequent creation and destruction
- same privileges
- no need to protect from each other
****
# Lecture 8

mutual exclusion of critical section
- Interrupt disables

Critical sections
- involves updates to object state
- multi-step operations (assembly)
- correct operation requires mutual exclusion

Don't share things you don't need to share
****
# Lecture 9 Semaphores and Other Synchronization Primitives

pthread_cond_braodcast: waking all blocked threads
- can be wasteful

Waiting list can cause race condition 
- Thread A tries to hold the lock by calling sleep function. while calling the function, context switch occurs. Thread B which had the lock gives up the lock by calling wakeup. Back to Thread A in sleep function. Thread A puts itself to sleep but there's no one to wake him up since Thread B already called wakup function.

Mutual exclusion: Only allow one of several activities to happen at once.
- locks
Asynchronous completion: There are things happening at different timing. 
We want to make sure the order in which things happen is proper.
- spinning and completion events

Semaphores: synchronization mechanism
- An integer counter
- FIFO waiting queue

P (proberen/test)
- Decrement counter, if count >= 0, return
- if counter < 0, add process to waiting queue

V (verhogen/raise)
- Increment counter
- If queue non-empty, wake one of the waiting process

lock -> initialize semaphore count to one
notification -> initialize semaphore count to zero
counting semaphores -> initialize semaphore count to the number of available resources

Mutexes: Linux locking mechanism
- good for brief durations, operations in a single address space
- bad for persistent objects (files) 

flock(file descriptor locking)
- Mutexes and flock() are advisory locks 
Enforced locking
Advisory locking
- gives users flexibility in what to lock and when
- gives users more freedom to do it wrong 

lockf(fd, cmd, offset, len)
- you can lock entire or portion of a file
- locking may be enforced

Blocking is much more expensive than getting a lock

convoy: list of processes that cannot run, waiting for the resource
- parallelism is eliminated
- convoy happens more likely with longer critical section

Convoy formation
$$P_{conflict} = 1-(1-\frac{T_{critical}}{T_{total}})^{threads}$$
$(1-\frac{T_{critical}}{T_{total}})^{threads}$ : nobody in critical section at the same time

Priority Inversion
$\rightarrow$ When lower priority task runs but higher priority task waits

Reduce Contention
- multiple processes trying to get the lock\
- eliminate preemption during critical section
****
# Lecture 11

most peripherals are attached to a bus

Device drivers
- specific to the particular device
- Inherently modular
- interacts with the rest of the system in limited ways
- implements standard behavior

Pictorial view

user space : apps
****
kernel space: device drivers 
****
hardware: actual bus (USB bus, PCI bus, etc)

Core OS code vs Device Drivers
- Common functionality belongs in the OS
	- Caching, file systems, network protocols
- specialized functionality belongs in the drivers
	- things that differ in diff pieces of hardware

Devices are not processes. they are piece of code. And they are ran by interrupts.

Devices communicate with CPU through the bus
- Devices and CPU are both connected to the bus
- Interrupt can be held pending until software is ready unlike traps

Direct Memory Access (DMA)
good for large transfer

Memory mapping
better for frequent small transfers

Device Driver Interface(DDI)
- High-end services drivers provide to OS

Driver/Kernel interface (DKI)
- bottom-end services OS provides to drivers