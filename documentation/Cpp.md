# Native Compilation G++ Compiler, Hello World

```sh
    root@edison:~# g++
    g++: fatal error: no input files
    compilation terminated.
    root@edison:~# vi helloworld.c
```

```c++
#include <stdio.h>

void main (){
    printf("Hello World\n");
}
```

```sh
    root@edison:~# g++ -o helloworld helloworld.c
    root@edison:~# ./helloworld
    Hello World
    root@edison:~# 
```