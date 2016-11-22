# Containers

# LinuxContainers.org 

> Infrastructure for container projects. The goal is to offer a distro and vendor neutral environment for the development of Linux container technologies. Our main focus is system containers. That is, containers which offer an environment as close to possible as the one you'd get from a VM but without the overhead that comes with running a separate kernel and simulating all the hardware. This is achieved through a combination of kernel security features such as namespaces, mandatory access control and control groups.

## LXC
> LXC is the well known set of tools, templates, library and language bindings. It's pretty low level, very flexible and covers just about every containment feature supported by the upstream kernel.

## LXD

> LXD is the new LXC experience. It offers a completely fresh and intuitive user experience with a single command line tool to manage your containers. Containers can be managed over the network in a transparent way through a REST API. It also works with large scale deployments by integrating with OpenStack.

## LXCFS

> Userspace (FUSE) filesystem offering two main things:
> - Overlay files for cpuinfo, meminfo, stat and uptime.
> - A cgroupfs compatible tree allowing unprivileged writes.
> 
> It's designed to workaround the shortcomings of procfs, sysfs and cgroupfs by exporting files which match what a system container user would expect.

More »



# Resin.io

> Resin.io brings the benefits of Linux containers to the IoT. Develop iteratively, deploy safely, and manage at scale. [Homepage](https://resin.io/)

- [ResinOS 2.0 Announcement](https://resin.io/blog/introducing-resinos/)
- [Hackerboards Resin.io](http://hackerboards.com/open-source-resinos-adds-docker-to-armlinux-boards/)