# kernel
- load first, always run, run serperately
- this central component of a computer system is responsible for '__running__' or '__executing__' programs
- the kernel takes responsibility for __deciding__ at any time which of the many running programs should be allocated to the processor or processors 
- the kernel is a computer program at the core of a computer's operating system with complete control over __everything__ in the system

## kernel vs user's software
- application programs like browsers, word processors, or audio or video players use a separate area of memory, __user space__
- this separation prevents __user data__ and __kernel data__ from interfering with each other and causing instability and slowness
- as well as preventing malfunctioning application programs from crashing the entire operating system

## kernel process
- the kernel's __interface__ is a low-level abstraction layer
- when a process __requests a service__ to the kernel
- it must invoke a __system call__
- usually through a wrapper function that is exposed to userspace applications by __system libraries__ which embed the __assembly code__ for entering the kernel after loading the __cpu registers__ with the __syscall__ number and its parameters (unix-like operating systems accomplish this task using the c standard library)

## kernel architecture
- __monolithic kernels__ run entirely in a single address space with the cpu executing in supervisor mode, mainly for speed
- __microkernels__ run most but not all of their services in user space, like user processes do, mainly for resilience and modularity
- linux kernel is monolithic, although it is also __modular__, for it can insert and remove loadable kernel modules at runtime

