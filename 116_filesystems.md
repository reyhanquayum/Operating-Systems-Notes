# File Systems 1

## Last class
* Performance characteristics
    * sequential access is much faster than random access
        * this bc u only need to seek once instead seeking each time for random access (seek time)
    * everything with file systems is predicated on sequential access

## File System

### Primary Use
* read + wrtie data in device with **persistent storage**
* persistent storage - storage that survives a process exiting or computer shutting down
* disk linear array of blocks u can address
    * build a file system, decide what space to use, allocation, figure out how to manage that space, what part of disk to give, when to erase/free, etc.
    * human names mapped to data

### File descriptor
* when file opened, ```fd = open("/tmp/out.txt, ...)``` the call goes to process PCB and goes to find open space in the file descriptor array to open it

### pages vs blocks
* same thing really - pages for mem, blocks for disk
* just disk is expected to survive power failure


### Allocation ways
#### a) Contiguous Allocation
* issue is when you want to access a particular offset in b, wasting time getting from a to be

#### b) Linked Files



