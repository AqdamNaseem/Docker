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

The following figure provides a detailed illustration of virtualization via containers. Note that the virtualization layer (containers and container engine) sits on top of the infrastructure layer and depends on certain parts of the operating system/kernel.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Containerization.png">
</p>

The following figure shows a hybrid container architecture that uses virtualization by both virtual machines and containers.

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Hybrid.png">
</p>

## Containerization vs Virtualization (via traditional hypervisors)

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Difference.png">
</p>

<p align="center">
<img src="https://github.com/AqdamNaseem/Docker/blob/master/images/Description.png">
</p>

Containers are becoming more widely used because they provide many of the isolation benefits of VMs without as much time and space overhead.

Although containers are typically hosted on some version of Linux, they are also now hosted on other operating systems, such as Windows and Solaris.

The traditional hypervisors like VMware, Virtual Box, etc can run on Windows, Linux as well as all those operating systems that support hypervisors.

Another difference is that containers share the same kernel as the host machine which is not in the case of hypervisors.

## Pros of Virtualization via Containers

The following advantages have led to the widespread use of virtualization via containers:

__Hardware costs__. Virtualization via containers decreases hardware costs by enabling consolidation (i.e., the allocation of multiple applications to the same hardware improves hardware utilization). It enables concurrent software to take advantage of the true concurrency provided by a multicore hardware architecture. In addition, it enables system architects to replace several lightly-loaded machines with fewer, more heavily-loaded machines to minimize SWAP-C (size, weight, power, and cooling), free up hardware for new functionality, support load balancing, and support cloud computing, server farms, and mobile computing.

__Reliability and robustness__. The modularity and isolation provided by VMs improve reliability, robustness, and operational availability by localizing the impact of defects to a single VM and enabling software failover and recovery.
Scalability. A single container engine can efficiently manage large numbers of containers, enabling additional containers to be created as needed.

__Spatial isolation__. Containers support lightweight spatial isolation by providing each container with its own resources (e.g., core processing unit, memory, and network access) and container-specific namespaces.
Storage. Compared with virtual machines, containers are lightweight with regard to storage size. The applications within containers share both binaries and libraries.

__Performance__. Compared with virtual machines, containers increase performance (throughput) because they do not emulate the underlying hardware. Note that this advantage is lost if containers are hosted on virtual machines (i.e., when using a hybrid virtualization architecture).
Real-time applications. Containers provide more consistent timing than virtual machines, although this advantage is lost when using hybrid virtualization.

__Continuous integration__. Containers support Agile and continuous development processes by enabling the integration of increments of container-hosted functionality.
Portability. Containers support portability from development to production environments, especially for cloud-based applications.

__Safety__. Safety is improved by localizing the impact of faults and failures to individual containers.
Security. The modular architecture provided by the containers increases the complexity and difficulty of attacks. Spatial isolation largely limits impact of malware to a single container. A container that is compromised can be terminated and replaced with a new container that is booted from a known clean image, which enables a rapid system restore or software reload following a cybersecurity compromise. Finally, security software and rules implemented at the container engine level can apply to all of its containers.

## Cons of Virtualization via Containers

Although there are many advantages to moving to virtualization via containers, architects must address challenges and associated risks in the following six areas:

__Shared Resources__. Applications within containers share many resources including (1) container-specific resources including the container, container engine, and OS kernel, (2) virtualization by VM resources including the virtual machine, the hypervisor, and the host operating system if using a type-2 hypervisor, and (3) multicore processing resources including (a) processor-internal resources (L3 cache, system bus, memory controller, I/O controllers, and interconnects) and (b) processor-external resources (main memory, I/O devices, and networks). Such shared resources imply (1) single points of failure exist, (2) two applications running in the samecontainer can interfere with each other, and (3) software running in onecontainer can impact software running in anothercontainer (i.e., interference can violate spatial and temporal isolation).

__Interference Analysis__. Shared resources imply interference. Virtualization via containers increases the difficulty of the analysis of temporal interference (e.g., meeting timing deadlines) and tends to make the resulting timing estimates overly conservative. Interference analysis becomes more complex as the number of containers increases and virtualization via containers is combined with virtualization via VMs and multicore processing. The number of interference paths increases rapidly as the number of containers increases. The resulting large number of interference paths typically make the exhaustive analysis of all such paths impossible. This, in turn, forces the architect to select only a relatively small representative selection of paths. 

__Safety__. Although containers provide significant support for isolation, the use of containers does not guarantee isolation. Temporal interference may cause delays that cause hard, real-time deadlines to be missed. Spatial interference can cause memory clashes. Whether by VM or containers, traditional safety accreditation and certification processes and policies do not take virtualization into account, making safety (re)accreditation and (re)certification difficult.

__Security__. Containers are not by default secure and require significant work to make them secure. One must to ensure that (1) no data is stored inside containers, (2) container processes are forced to write to container-specific file systems, (3) the container's network namespace is connected to a specific, private intranet, and (4) the privileges of container services are minimized (e.g., non-root if possible). As with safety, traditional security accreditation and certification processes and policies do not take virtualization into account, making security (re)accreditation and (re)certification difficult.

__Container Sprawl__. Excessive containerization is relatively common and increases the amount of time and effort spent on container management.

## Docker overview
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production

Docker provides the ability to package and run an application in a loosely isolated environment called a container. The isolation and security allow you to run many containers simultaneously on a given host. Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. This means you can run more containers on a given hardware combination than if you were using virtual machines. You can even run Docker containers within host machines that are actually virtual machines!

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
