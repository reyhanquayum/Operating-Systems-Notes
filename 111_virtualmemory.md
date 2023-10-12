# Virtual Memory (as opposed to physical memory)
## why?
* system to run multiple programs
* makes it easy to reason about your program
    * programs don't interact or mess up other programs
* **security** - memory isolation make it harder for programs to look at other memory

## Position Independence
* make assumptions about the layout
    * code is loaded into some address, (address 500 is different for program A than program B)

## Overcommit
* allow processes to access more memory than physically available 

## Controlled sharing
* isolation important until you want programs to *start* communicating w/ eachother
* to share some memory, need controlled
* **sharing** - both processes agree to
    * share memory
    * set permissions
* eg. printf() executed by my code and your code is the same, it's shared code

## MMU (Memory Management Unit)
 * responsible for deciding what physical RAM address does a hex address (0X7FF2000) translate to
 * configuration determines translation
 * every address you see (like in gdb or in instructions) are **virtual** addresses, almost never worrying about physical addresses unless writing device drivers or something else vvvv

 ### MMU configuration
 * %cr3 *intel naming convention* address of the **page table**
    * **page teable** - array that goes from 0 to max valid address can used by machine
* Q: *What is a segfault?*
* A: *operating system gets an exception that you're trying to address memory address 0 (unmapped part of array)*