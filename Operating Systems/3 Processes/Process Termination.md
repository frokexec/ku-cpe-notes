# Process Termination

A process terminates when it finishes executing its final statement and asks
the operating system to delete it by using the `exit()` system call.

- Return child status to parent
- Process's resources are deallocated by OS.

Parent may terminate the execution of children processes using `abort()` system call for

- Child has exceeded allocated resources
- Task assigned to child in no longer required
- The parent is exiting (**cascading termination**)

## Zombie Process

A process that has completed its task but the parent is not reading the process state. In the other words, if no parent waiting process is a **zombie**

## Orphan Process

If parent terminated without invoking `wait()`, process is an **orphan**

See <https://www.geeksforgeeks.org/difference-between-zombie-orphan-and-daemon-processes/>
