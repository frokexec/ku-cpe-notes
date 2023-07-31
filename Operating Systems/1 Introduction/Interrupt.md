# Interrupt

An interrupt is a signal emitted by hardware or software when a process or an event needs immediate attention.

## Common Functions of Interrupts

- Through the **[[Interrupt vector]]**, which contains the addresses of all service routines.
- Interrupt architecture muse save the address of the interrupted instruction
- A trap or exception is a software-generated interrupt caused either by an error or a user request
- An OS is **interrupt driven**

## Examples (from ChatGPT)

1. User presses a key on the keyboard.
2. The keyboard hardware sends an electrical signal to the computer's CPU to indicate that a key has been pressed.
3. The CPU receives the interrupt signal and temporarily suspends the currently executing process.
4. The CPU transfers control to the interrupt handler routine specific to keyboard interrupts.
5. The interrupt handler reads the key code from the keyboard controller, processes it, and stores it in a buffer (main memory).
6. If there is a process waiting for keyboard input, the interrupt handler wakes up that process and provides it with the input data.
7. The interrupt handler updates the state of the system, such as updating the display or triggering specific actions based on the key pressed.
8. Once the interrupt handler completes its task, it returns control to the interrupted process.
9. The interrupted process resumes execution from where it was paused, continuing its normal operation.

## Interrupt Timeline

![[Pasted image 20230716205259.png]]

1. I/O device sends an interrupt signal (IRQ | Interrupt Request) to CPU
2. If CPU is in EI (Enable Interrupt) state, it will response to the IRQ and send back Interrupt Acknowledge to the device
3. The CPU will set its state to DI (Disable Interrupt)
4. It will stop processing the running program
5. The device sends **[[Interrupt Vector]]** to CPU
6. Move the data from PC registers and common registers to stack
7. Process the subprogram to serve the device that send the IRQ
8. Move the data form stack back to PC registers and registers
9. Set the CPU state back to EI (Enable Interrupt)
10. Continue to process the running program

## Interrupt types

Interrupts can be split into categories depending on what triggered them:

- exceptions - triggered by the CPU itself
- IRQs - triggered by external hardware (e.g. network card)
- software interrupts - triggered explicitly by the code that was running
- IPIs (inter-processor interrupts) - triggered by a different CPU

Exceptions can be further broken down into sub-categories:

- aborts - things that prevent the interrupted code from continuing. These are things that indicate a major problem - e.g. division by zero, hardware failures, etc.
- traps - things that don't prevent the interrupted code from continuing. These can be used for debugging, for virtual memory management, etc.

## Interrupt-drive I/O Cycle

![[Pasted image 20230716205745.png]]
