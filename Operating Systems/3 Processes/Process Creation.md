# Process Creation

Parent process create children processes, forming a tree or processes.
Process is identified and managed via a **process identifier** (PID).

## Resource sharing options

```
- Parent and children share all resources
- Children share subset of parent's resources
- Parent and child share no resources
```

## Execution option

- Execute concurrently
- Parent waits until children terminate

## Address space

The range of virtual addresses that the operating system assigns to a user or separately running program

- Child duplicate of parent
- Child has a program loaded into it

## UNIX examples

- `fork()` system call creates new process (copy of the parent process)
- `exec()` system call used after `fork()` to replace the process' memory space with a new program
- Parent process calls `wait()` waiting for the child to terminate

## Tree or processes in Linux

See `pstree`

![[Pasted image 20230720092536.png]]
