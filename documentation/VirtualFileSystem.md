# Virtual File System

> A virtual file system (VFS) or virtual filesystem switch is an abstraction layer on top of a more concrete file system. The purpose of a VFS is to allow client applications to access different types of concrete file systems in a uniform way.  [Wikipedia](https://en.wikipedia.org/wiki/Virtual_file_system)

> The Linux kernel implements the concept of Virtual File System (VFS, originally Virtual Filesystem Switch), so that it is (to a large degree) possible to separate actual "low-level" filesystem code from the rest of the kernel. [The Linux Virtual File System](https://www.win.tue.nl/~aeb/linux/lk/lk-8.html)

> In Linux, all files are accessed through the Virtual Filesystem Switch, or VFS. This is a layer of code which implements generic filesystem actions and vectors requests to the correct specific code to handle the request. Two main types of code modules take advantage of the VFS services, device drivers and filesystems. [A tour of the Linux VFS](http://www.tldp.org/LDP/khg/HyperNews/get/fs/vfstour.html)

> In order to support multiple filesystems, Linux contains a special kernel interface level called VFS (Virtual Filesystem Switch). This is similar to the vnode/vfs interface found in SVR4 derivatives (originally it came from BSD and Sun original implementations). [Virtual Filesystem (VFS)](http://www.tldp.org/LDP/lki/lki-3.html)

- [A tour of the Linux VFS](http://www.tldp.org/LDP/khg/HyperNews/get/fs/vfstour.html)


