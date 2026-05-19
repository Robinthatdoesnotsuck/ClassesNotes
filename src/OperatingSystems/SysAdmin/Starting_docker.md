# Containers and using docker

So first what is a container?

## A container is...

Let us first think about the issues of using vms as we were using them accross the whole course.
A VM is a emulation of first the hardware layer of a computer and then the SO part of it, making it an isolated system first by hardware.
With this we would have a reproductible linux or whatever OS environment that we can port to another host that has the virtualization engine use
to virtualize it in the first place.

Now enter containers, the main issue with VMS is the weight, time to start, time to die and mostly the efficiency of use of the computing power since we also
emulate the hardware and well containers don't have this issue or minimize most of this issues.

Containers in essence can be viewed as VMs more closely to programs than full fledge emulations, they are an isolated environment runtime with the minimum requirements
to run an Operating System like any flavor of linux.

But what does this really means?

Well that containers having the minimum requirements to run a linux environment, use the minimum of resources to do so, or as much to do so. BUT They are not without their caveats like:

- Not being persisent
- Not having any complex tooling aside the base ones pre-installed
- Not having any sort of ui

So why would we be using this instead of regular VMs?

Well cause they are way better at the things that make VMs good actually, they are more portable, more resource efficient and way easier to start/shutdown depending on what you need.

So if they are so muuuuch better why use vms at all?

Well for the reasons already pointed earlier, like what if we need a more complex system to emulate or a even more isolated way to separate OS, adding a UI, better and stabler persistance, etc.

## Using containers

### Firsts steps

Install docker desktop or just docker in your OS, it will give you a neat tidy UI to use and administer your containers

