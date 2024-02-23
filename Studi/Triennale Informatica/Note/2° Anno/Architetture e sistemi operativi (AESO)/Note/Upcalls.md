---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Upcalls
---


le upcalls sono sistemi per permettere ai processi di avere funzionalità simili ai [[Sistemi Operativi]], ad sempio:

- **Preemptive user-level threads**. Just as the operating system kernel runs multiple
processes on a single processor, an application may run multiple tasks, or threads, in
a process. A user-level thread package can use a periodic timer upcall as a trigger to
switch tasks, to share the processor more evenly among user-level tasks or to stop a
runaway task, e.g., if a web browser needs to terminate an embedded third party
script.
- **Asynchronous I/O notification**. Most system calls wait until the requested operation
completes and then return. What if the process has other work to do in the meantime?
One approach is asynchronous I/O: a system call starts the request and returns
immediately. Later, the application can poll the kernel for I/O completion, or a separate
notification can be sent via an upcall to the application when the I/O completes.
- **Interprocess communication**. Most interprocess communication can be handled with
system calls — one process writes data, while the other reads it sometime later. A
kernel upcall is needed if a process generates an event that needs the instant
attention of another process. As an example, UNIX sends an upcall to notify a process
when the debugger wants to suspend or resume the process. Another use is for logout
— to notify applications that they should save file data and cleanly terminate.
- **User-level exception handling**. Earlier, we described a mechanism where processor
exceptions, such as divide-by-zero errors, are handled by the kernel. However, many
applications have their own exception handling routines, e.g., to ensure that files are
saved before the application shuts down. For this, the operating system needs to
inform the application when it receives a processor exception so the application
runtime, rather than the kernel, handles the event.
- **User-level resource allocation**. Operating systems allocate resources — deciding
which users and processes should get how much CPU time, how much memory, and
so forth. In turn, many applications are resource adaptive — able to optimize their
behavior to differing amounts of CPU time or memory. An example is Java garbage
collection. Within limits, a Java process can adapt to different amounts of available
memory by changing the frequency with which it runs its garbage collector. The more
memory, the less time Java needs to run its collector, speeding execution. For this, the
operating system must inform the process when its allocation changes, e.g., because
some other process needs more or less memory.

![[Untitled 32.png]]

![[Untitled 1 15 1.png]]

- **Types of signals**. In place of hardware-defined interrupts and processor exceptions,
the kernel defines a limited number of signal types that a process can receive.
- Handlers. Each process defines its own handlers for each signal type, much as the
kernel defines its own interrupt vector table. If a process does not define a handler for
a specific signal, then the kernel calls a default handler instead.
- **Signal stack**. Applications have the option to run UNIX signal handlers on the
process’s normal execution stack or on a special signal stack allocated by the user
process in user memory. Running signal handlers on the normal stack makes it more
difficult for the signal handler to manipulate the stack, e.g., if the runtime needs to
raise a language-level exception.
- **Signal masking**. UNIX defers signals for events that occur while the signal handler for
those types of events is in progress. Instead, the signal is delivered once the handler
returns to the kernel. UNIX also provides a system call for applications to mask signals
as needed.
- **Processor state**. The kernel copies onto the signal stack the saved state of the
program counter, stack pointer, and general-purpose registers at the point when the
program stopped. Normally, when the signal handler returns, the kernel reloads the
saved state into the processor to resume program execution. The signal handler can
also modify the saved state, e.g., so that the kernel resumes a different user-level task
when the handler returns.

il meccanismo per far funzionare i segnali UNIX è simile al meccanismo per passare il controllo da kernel a user
ù