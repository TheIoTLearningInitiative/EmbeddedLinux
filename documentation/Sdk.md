# Native SDK

> To cross-compile native applications for your image, you must generate an SDK containing a cross-compiler toolchain and sysroot. You can generate a full SDK for the Edison Development Board.

# Building via Make

```sh
    user@host:~$ make sdk
    user@host:~$ ls out/current/build/tmp/deploy/sdk/
    poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.manifest
    poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.sh
    user@host:~$ out/current/build/tmp/deploy/sdk/poky-edison-glibc-x86_64-edison-image-core2-32-toolchain-1.7.2.sh
```

# Building via BitBake

```sh
    user@host:~$ bitbake edison-image-c populate_sdk
    user@host:~$ ls tmp/deploy/sdk
    user@host:~$ poky-edison-eglibc-x86_64-edison-image-core2-32-toolchain-1.6.1.sh
```