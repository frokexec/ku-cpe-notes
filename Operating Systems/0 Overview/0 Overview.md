# 0 Overview

Table of Contents

1. [General Model of a Computer](#General%20Model%20of%20a%20Computer)
2. [How a computer starts?](#How%20a%20computer%20starts?)
3. [What is kernel?](#What%20is%20kernel?)
4. [How processes talk to each other?](#How%20processes%20talk%20to%20each%20other?)

## General Model of a Computer

User <-> Application <-> Operating System <-> Hardware

- User -> Application
	How does the user talk to an application?

- Application -> OS
	How does this application interact with the OS?

- OS -> Hardware
	How does the OS interact with the hardware?

- Hardware -> OS
	How does the hardware tell the OS that something is done or needs attention?

- OS -> Application
	How does the OS tell, send data to, or otherwise interrupt the application?

- Application -> User
	How does the application deliver it back to the user?

## How a computer starts?

BIOS(POST) -> MBR/GPT -> GRUB -> Kernel -> Init -> RunLevel
`OS-Independent` | `OS-Dependent (Linux)`

## What is kernel?

A layer inside OS that communicate the tasks between application and hardware
![[Pasted image 20230716182407.png]]

## How processes talk to each other?

- Pipelining `|` in UNIX
- stdin stdout stderr
