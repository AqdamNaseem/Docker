# Docker

## Virtualization
Virtualization is a collection of software technologies that enable software applications to run on virtual hardware (virtualization via virtual machines and hypervisor) or virtual operating systems (virtualization via containers). 

A virtual machine (VM), also called a guest machine, is a software simulation of a hardware platform that provides a virtual operating environment for guest operating systems. A hypervisor, also called a virtual machine monitor (VMM), is a software program that runs on an actual host hardware platform and supervises the execution of the guest operating systems on the 
virtual machines.

As shown by the following figure, there are two types of virtualization via VMs, based on the type of hypervisor used:

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Virtualization.png">
</p>

A type 1 hypervisor, also called a native or bare metal hypervisor, is hosted directly on the underlying hardware.
A type 2 hypervisor, also called a hosted hypervisor, is hosted on top of a host operating system.

## Containerization
Containerization is a lightweight alternative to a virtual machine that involves encapsulating an application in a container 
with its own operating system. A container takes its meaning from the logistics term, packaging container. When we refer to an application container, we mean packaging software.

In short a container is a virtual runtime environment that runs on top of a single operating system (OS) kernel and emulates an operating system rather than the underlying hardware.

A Container engine is a managed environment for deploying containerized applications. The container engine allocates cores and memory to containers, enforces spatial isolation and security, and provides scalability by enabling the addition of containers.

Containerization has recently gained hypes with an open source tool Docker. Docker containers are designed to run on every environment from physical computers to virtual machines, from bare-metal, Clouds, etc.

We can even have a hybrid architecture by combining virtualization by both virtual machines and containers, i.e., the container engine and associated containers execute on top of a virtual machine. Use of a hybrid container architecture is also known as hybrid containerization.

## Containerization vs Virtualization (via traditional hypervisors)
