vmlatency - GGG's Lame Virtual Monitor Meter. 
The code is based on the vmlaunch by Vish Mohan.
WARNING: the kernel module is completely unstable, may crash your system at random. 
Do not use. I told you.

vmlaunch
========

Simple Driver code for vmlaunch
The idea behind the driver is to demonstrate a real example of how to initialize 
the Virtual Machine Control Structure(VMCS) and to use Intel VT instructions to launch 
a virtual machine. The driver launches a guest (virtual machine) with vmlaunch, executes 
one instruction(that causes a vmexit) and then returns to the host. For the vmlaunch 
instruction to execute successfully, a lot of cpu state (host and guest state) needs
to be initialized all of which is done by this driver. The driver also takes a simple 
approach in setting up the guest state by making it mirror the host state. This makes 
the design much simpler - for instance the guest does not need its own CR3, it shares 
it with the host. Inline assembly is used generously throughout the driver.
