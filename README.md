# Docker

Docker uses the concept of Containerization.Containerization is often confused with Virtualization(with Hypervisors).Let us first understand what is virtualization and how containerization if different from Virtualization

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

The following figure provides a detailed illustration of virtualization via containers. Note that the virtualization layer (containers and container engine) sits on top of the infrastructure layer and depends on certain parts of the operating system/kernel.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Containerization.png">
</p>

The following figure shows a hybrid container architecture that uses virtualization by both virtual machines and containers.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Hybrid.png">
</p>

## Containerization vs Virtualization (via traditional hypervisors)
Containers are becoming more widely used because they provide many of the isolation benefits of VMs without as much time and space overhead.

Although containers are typically hosted on some version of Linux, they are also now hosted on other operating systems, such as Windows and Solaris.

The traditional hypervisors like VMware, Virtual Box, etc can run on Windows, Linux as well as all those operating systems that support hypervisors.

Another difference is that containers share the same kernel as the host machine which is not in the case of hypervisors.

| __Virtual Machines (VMs)__ | __Containers__ |
|----------------------------|----------------------------|
| Hardware Level Virtualization	| Operating System Virtualization |
| Heavyweight |	Lightweight |
| Slow Provisioning |	Real-time and fast provisioning|
| Limited performance	| Native performance |
| Fully isolated	| Process-level isolation |
| More Secure | Less Secure |

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Difference.png">
</p>

### Benefits of Containers
- Multi-Cloud Platform : One of the major benefit on Containers that it can operate on the cloud. They support a multi-cloud platform and can be run on AWS, GCP, Rackspace, and VirtualBox.
- Shares same OS : Containers share the same OS kernel as the host. So, containers can be more efficient than VM as it requires a separate OS to run.
- Testing and CI-CD : Containers are consistent throughout the application which modulates to an agile environment and the approaches like Continuous Integration and Continuous Delivery (CI-CD).
- Portability : Containers have better portability than other hosting technologies. The can move along any system. The container configuration is also portable as it is just a file to share.
- Version Control : This is one of the most important parts of the Software Development Life Cycle (SDLC). Docker offers version control that makes it easy to roll back to a previous image if your setup breaks.
- Cost-Efficient : Containers are also cost-efficient. In spite of investing in memory, CPU, and storage, it is possible to support many containers on the same infrastructure.
- Speed : Containers spins faster than VMs which is very important for distributed applications.
 

### Disadvantages of Containers
- Security Concern : As the containers share a host, the potential threats are easy to penetrate to the system due to the lack of isolation which is not much in hypervisor-based virtualization.
- Lack of Isolation : Another issue with a container is the lack of OS flexibility which means containers must be of the same OS as of the Base OS. While in hypervisor-based virtualization, even Windows OS is able to virtualize both Windows as well as Linux based OS.
- Monitoring : It is hard to monitor containers when hundreds of containers are running on the same server.
- Features : Most of the big features in containers are still in development phase like a security tracking system, monitoring system, etc.

## Docker overview
Docker is an open platform for developing, shipping, and running applications. It provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a given host. Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. This means you can run more containers on a given hardware combination than if you were using virtual machines. You can even run Docker containers within host machines that are actually virtual machines!

By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production

Docker provides tooling and a platform to manage the lifecycle of your containers:

- Develop your application and its supporting components using containers.
- The container becomes the unit for distributing and testing your application.
- When you’re ready, deploy your application into your production environment, as a container or an orchestrated service. This works the same whether your production environment is a local data center, a cloud provider, or a hybrid of the two.

## Docker Engine
Docker Engine is a client-server application with these major components:

- A server which is a type of long-running program called a daemon process (the dockerd command).
- A REST API which specifies interfaces that programs can use to talk to the daemon and instruct it what to do.
- A command line interface (CLI) client (the docker command).

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Docker.png">
</p>

## Docker architecture
Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Architecture.png">
</p>

__The Docker daemon__ : The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

__The Docker client__ :The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

__Docker registries__ :A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry. If you use Docker Datacenter (DDC), it includes Docker Trusted Registry (DTR).

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry.

__Docker objects__ : When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.

__IMAGES__ : An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

__CONTAINERS__ : A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

By default, a container is relatively well isolated from other containers and its host machine. You can control how isolated a container’s network, storage, or other underlying subsystems are from other containers or from the host machine.

A container is defined by its image as well as any configuration options you provide to it when you create or start it. When a container is removed, any changes to its state that are not stored in persistent storage disappear.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Architecture.png">
</p>

## How Docker works in Windows or Mac OS based System
In their current forms, Docker-on-Windows and Docker-on-Mac are somewhat less clunky than the earlier iteration. Previously, using Docker on these systems required users to run VirtualBox virtual machines(Docker Toolbox). Now Docker uses hypervisors native to the respective operating systems. Those hypervisors are xhyve on OS X and Microsoft Hyper-V on Windows. They take the place of VirtualBox.

Docker is making much of the fact that its containers now can run on Windows and OS X using native hypervisors. The change does streamline things a little bit, since it makes it easier to integrate Docker environments on these platforms more tightly into the host operating system. Combined with the bundling of Docker development tools into the Windows and OS X Docker packages, developers now have a one-stop shop for running Docker containers on these systems.

But these updates do not really amount to much. At the end of the day, Docker on Windows and OS X still runs inside a Linux virtual machine. (Specifically, it uses the lightweight Alpine Linux distribution.)

That means when Docker says you can run Docker containers on Windows or OS X, it’s not exactly true. You’re still running them on top of Linux, using a Linux virtual machine that runs on top of Windows or OS X.

And when you throw a virtual machine into the mix, you lose efficiency. True, Alpine Linux is not exactly a resource hog. The overhead it adds to a Docker system is relatively negligible, especially on modern machines. But it’s overhead all the same.
