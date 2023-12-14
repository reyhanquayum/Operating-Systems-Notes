# Final Review

## Virtual Memory
* distinction between phyhsical and virtual addresses 
* kernel sets up demand paging, where is the data that should be contained in the page, how doe sit remember what the data is? remember that you set the metadata and the kernel can keep additional data structures to remember this. the page corresponding
* so normally i dont need this demand paging thing means that if i wanted a process to make progress i only need to keep enough pages so that it has a stack and its executing code and any data that the executing code is operating on 4-5 pages it has to fetch the page you can use this trick to increase the amount you can tell the process hey pretend you have 8 GB of RAM even tho the actual is 2 GB some accesses take a lot of time because of demand paging because you have to fetch the page which is why you're able to do this. the process believes it has 8 GB of space, and as time goes on i have to ge trid of pages from memory, several policies decide which pages to evict. evict means you take its contents and write it to disk so you have it available later. we talked about FIFO, it can get arbitrarily bad performance, and LRU (least recently used) and another policy. 


## page faults
 * useful to understand how given vrirtual memory and page faults oyu can make this memory expansion work and use for other things and figure out how many times an applicated accesses a page

 ## TLB
 * look a side buffer
 * used for performance and easy question we ewalked thru is how to come up with programs that always have TLB misses or hits
 * how to maximize TLB misses
    * a cache has finite capacity, and by design mos tcaches have less capacity than the underlying system they're caching (obviously)
    * oh, this virtual mmeory maps to this phys mem
    * you have a TLB that can cache 4 virtual mem addresses
    * suppose ur program addresses 5 virtual mem addresses
    * can you do ... without incurring a miss you can only remmeber 4 of them, when you need the fifth i must get rid of one of the ones i had from before. i can't have 5 of them all loaded up. right
    * TLB misses **NEVER** cause a page fault
    * page fault only happens if valid bit is not set or you are trying to do an incorrect access


## copy on write
* reuisng demand paging mechanism and why you do it
* implement in both user space and kernel
* what weesny os was doing

## explicit I/O instructions
* two questions that come up when you deal with IO devices
* 1) how to transfer data to and from device
* explicit I/O instructions
* these can read a byte at a time or 64 bits at a time and took a port number (ID) 
* **MMIO** when we were talking ab virtual memory, we pretend that all phys memory corresponds ot things on the RAM, but even in laB 4 some o f the memory was the console page, it wasn't about any physical RAM
    * is a physical address but to access it
    * no program except kernel can access a physical address so a program has to provide virtual address that maps to that physical address 
    * benefit is that is has lower latency than DMA but processor is actually doing work to transfer this data 

* **DMA** hey the data you'r elooking for is physical space in RAM this is the physical address where you can fetch data from. 
    * thing that is nice is that it's asynchronous, processor doesn't have ot do any memcopyes

* **interrupts** in all 3 of these maechanisms when is it safe to do interrupts

* **polling** process sitting there and constantly asking hey are u done are u done

* **device drivers** - just know what they are 

* **blocking vs non blocking I/O** 
    * just know what they are

## Disks

* **Sectors, tracks, cylinders**
    * mechanical or spinny disks
    * disks comprise of platters, each platters has concentric circles called tracks, each track has middle units that we call sectors, the cylinder is  just the stack of tracks that lie one on top of another
    * when reading from this disk we have a head and tr yto mechanically move to the right sector that move is called **seek time**
    * one head per platter, only horizontal movement
    * **rotational delay** this thing is moving very fast this sector might be on the other side so i wait until it's under the head then after i've read it the disk needs to transfer to the computer and this is **transfer time** - MB/s
        * average rotational delay (avg time ittakes for sector to arrive under read head)
    * how long does it take to make one rotation you can figure out
    * half of that time is basically the amount of delay for rotational delay (7200 RPM)
    * seek time is also an average that is a physical thing that is the amt of time that takes from innnermost concentric circle to outermost concentric circle, it's a bit more complicated, seeking a disk first accelerates then it coasts then slows down, so it's too hard to think, so we do average
    * notion of **blocks** we always read/write to disk in 4 KB blocks! (lab)
    * if i tell u ur disk in random place and u wanna read blcok 55 then the cost of reading it is gonna be you have to seek bc it's an arbitrary place, u gotta go to right track, then you pay rotational delay, then you pay transfer time cost for 4KB

    * **sequential vs random access**
        * disk accesses randomly, never get any benefits from where the disk head is
        * sequential access head is already in a place, then the part i wanna read is kinda close then the benefit is that the head is alr on the correct track we don't have to seek further and we don't pay rotational delay 

## File Systems

* interface 
    * open
    * read/ write
    * mmap
        * user space where we fake having more memory
    * lseek
        * when u open a file what the file descriptor table keeps track of is that there is a file descriptor
* representing files
    * metadata is just basically what any file is, permissions who owns it 
    * data layout trade offs
        * contiguous allocation - when u get a file u declare my file is 500 blocks or whatever and it puts them all together
        * linked - is just a linked list 
        * indexed - what we did in the lab, build a tree index indirect double indirect blocks and u can just keep increasing file size down the path 
    * **inode**
        * direct blocks
        * indirect blocks
        * double indirect

* **directories**
    * name comes from dirent that represennts it
    * that's why we have a referenec count that keeps track of link count delete file when it gets to zero

**REvvIEW CRASH RECOVERTY AND COPY-ON WRITE!**

* stack smashing
    * not how to do it
    * stack (from before midterm) frame
    * inject code

* every file in inode records unix uid and gid check file permissions 
* setuid 

# trusting trust
* conceptual issues, JUST KNOW IT, don't DISreGaRd It
* do we need to know the code or just conceptual ummm
    * WE DON'T NEED TO KNOW THE CODE!!! YAY
* IT'S NOT JUST KNOWING THE BOOTSTRAP COMPILER
* it more the general idea because you can learn behavior or in general the behavior of a program depends not only on program code but also depends on OS and hardware and compiler and other dependencies

# putting it all toegetherther
* execve
    * mapping and unmapping 
* loading executables
    * useful to know what it is

* we DON'T ENEED TO NKOW THE DETAILS!
* need to know what these things are 