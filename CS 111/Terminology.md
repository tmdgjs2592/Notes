**PTE**: Page Table Entry
**PFN**: Page Frame Number
**TLB**: Translation Lookaside Buffer
- memory cache that stores the recent translations of virtual memory to physical memory

**Three C's**
- Compulsory miss: misses that result from the emptiness of a cache
- Capacity miss: misses that occur from full capacity
- Conflict miss: misses that occur because of limits on where an item can be placed in a hardware cache.

**PCB**: Process Control Block
**TCB**: Thread Control Block
- to store the state of each thread of a process

**Critical Section**: code that accesses a shared resource -- variable or data structure.
**Race Condition**: when multiple threads of execution enter the critical section at roughly the same time -- leading to an unexpected outcome.
**Indterminate program**: program that consists of one or more race conditions -- not deterministic.
**Mutual exclusion primitives**: primitives that allow only a single thread into a critical section.