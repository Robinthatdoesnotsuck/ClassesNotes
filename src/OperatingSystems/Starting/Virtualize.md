# What does a good operating system do?

## It Lies to us (Like a man)

An operating system main purpose is to gives us an easy way to use a computer, to do this our main OS of choice(linux) uses an assortment of tools and techniques to gives a ready to use OS.

## Virtualization

Virtualization is the act of abstracting the hardware to something digital to be used by a user. This means the OS gives us the tools to use hardware safely, agnostic of vendor, type, etc. This gives us full control of our computer without the hasle of reinventing interfaces to communicate to devices such as the screen, keyboard, connections ports, GPU, etc. Cause in the time before time itself engineers had to re-program interfaces to be able to use their hardware and that is a pain in the ass.

### CPU

The first of the main components that the OS virtualize is our CPU or at least the way the CPU is handled cause look at this way, what happens when I have a bunch of food for multiple animals but only one plate at least in the idea of OS managing the CPU time is by lying to them in way that we tell them "Don't worry I promise you will eat(But we don't know at what time it will eat)", this is the basis of CPU virtualization, the OS lies to a program by promising it processing time on the CPU at a point in time.
But you'll say, hey doesn't that lives us with a really big line of sequential programs waiting in line? Yep and the OS solves that problem by doing something called context switching, this means that it will stop a program while executing, save the state of the program, then start another program, but you need to know a single CPU goes and changes the execution of programs millions of times a second, so [IT GIVES US THE ILLUSION](https://youtu.be/uY4cVhXxW64?t=76) of parallelism and that illusion is called concurrency.

### Memory

Now with memory, The second component the OS handles for us in a perfect way, now when handling memory(by that I mean RAM) the OS will lie to the program the amount of memory by just giving it a small portion of physical memory to it, so be it that the physical memory is actually randomly assigned, but virtualy it isolates each programs memory into something called ADDRESS SPACE, if you are familiar with pointers you might know that a pointer gives a reference in hexadecimal of the position in memory of data, well this hexadecimal number might be the same between programs and this is not an error is the OS working its ILLUSION, the OS handles all the weird sheananigans of assigning physical memory where it will be free, but to us we only see the virtualized version, that is why if you do an stackoverflow error in a normal program in your computer it will overflow the memory OF THAT PROGRAM not of the whole system.

<img src="https://i.pinimg.com/736x/06/04/9b/06049b49ba785bd44ad33e0e7683654d.jpg" alt="placeholder" width="60%" height="60%">

### Persisting (This means just saving data on a disk)

Okay so RAM is something called Random Access Memory and it is also called volatile memory, this means that if I unplug the power source, the memory saved inside it will be lost and now this will be a big bummer, how can I use the computer if the work I do wasn't saved in the first place. Here comes persistence, persistence is the action of saving data or state inside a non-volatile memory, like a hard drive, sdd, sd-card, disk, etc. The OS also virtualize this device for ease of use cause if you wanted to save say by hand something inside a hard-drive it would be a grueling task of learning how the device works, then checking free space, then writing into free space and so on until you saved something, the os just kinda saves it using a set of tools that we will discuss later in the course.

## How programs work inside an operating system

So know we know the essential tasks of the OS let us rip apart those task to fully understand what the hell is going on and how the OS accomplish this

### Processes and Jobs

So What is a program in the context of an Operating System? The answer to that question is that running programms are Processes or Jobs, each one different from the other and with the help of the operating system virtualization task they will acomplish their job.
First a program is created, then executed, then dead(this will happen either if it succeeds or fails) this is the lifecycle of a program in general, but it will change states to fullfil this lifecycle. Let us say a basic c++ program like this is going to be executed:

```c++
int main() {
    return 0;
}
```

At creation the program starts at the Ready state, meaning that the program can execute but it is waiting for the OS to decide on this. Then the OS will give it time to execute this is the Running state, this means that the program is running its instructions inside the CPU, then it might do some action that interrupts it like writing to a file, printing something to the standard I/O this state is what we call Blocked after doing any operation that is dependant on another event it will enter the ready state and so on so on the state changes continue. This is the basic way a program behaves inside OS.
