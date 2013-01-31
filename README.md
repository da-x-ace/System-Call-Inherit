System-Call-Inherit
===================

In Linux, accessing the sys call table by user process or even LKM (Lodable
Kernel Module) is not possible. And in order to add a new system call we
need to add an entry in the syscall:h. But there can be a need of adding
new functionality in form of system calls. So, we need an implementation for
providing that functionality. We came accross many ideas for implementing
this e.g.
(a) creating a new system call for this purpose,
(b) intercepting system calls in user level library,
(c) overriding the global system call table.
Among these three, we decided to go with the last one, as it seemed rea-
sonably better in accordance to what we aim to achieve. It is sometimes
required that an application wants its processes to use a set of system calls
only and might want their own implementation of those system calls, e.g.
An application while calling exec() might want to log this information in a
le, so we can wrap their exec() syscall to do this task.
Now, if we want to override the global system call table then we need
to identify which process needs what additional functionality. We can't just
create another syscall table and ask our process to use that if they needed
additional functionality. We needed a way to generalise it. So, we decided
to create new overridden system call tables on per process basis. As this
provides user specic functionalities.


Code will be provided on demand.

Mail to: prankur[ d o t ]07[ a t ]gmail[ d o t]com.
