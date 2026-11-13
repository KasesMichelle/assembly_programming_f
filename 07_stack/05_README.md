05.asm – 64-bit Stack Operations

1. Introduction

This program demonstrates how 64-bit values are stored and retrieved using PUSH and POP instructions.

It illustrates how the stack temporarily stores register values and how the LIFO principle determines the order in which values are retrieved.

2. Program Execution Flow

Step 1: Loading Values

Execution begins at _start.

mov rax, 0x1122334455667788 loads a 64-bit hexadecimal value into RAX.

mov rbx, 0x1234 loads another value into RBX.

These instructions do not affect RSP.

Step 2: Pushing Values onto the Stack

push rax stores the value 0x1122334455667788 on the stack.

push rbx stores 0x1234 on top of the previous value.

Each PUSH decreases RSP by 8 bytes.

The second value becomes the topmost stack element.

Step 3: NOP Instruction

The nop instruction does nothing. It provides a point where the stack contents can be inspected.

Step 4: Popping Values

pop rbx retrieves 0x1234 into RBX.

pop rax retrieves 0x1122334455667788 into RAX.

Each POP increases RSP by 8 bytes.

The values are restored to their original registers.

Step 5: Program Termination

mov rax, 60 selects the Linux exit system call.

xor rdi, rdi sets the exit status to zero.

syscall terminates execution.

3. Stack Pointer Changes

Let the initial RSP be S.

Instruction

RSP

Initial state

S

PUSH RAX

S - 8

PUSH RBX

S - 16

POP RBX

S - 8

POP RAX

S

The stack pointer returns to its original value after the two values are retrieved.

4. Observations

The program executes successfully with exit status 0.

No terminal output is produced because the program only manipulates registers and stack memory.

After the POP operations:

RAX contains 0x1122334455667788.

RBX contains 0x1234.

RSP returns to its original position.

This confirms that the stack follows the LIFO principle.

5. Conclusion

The program demonstrates how the 64-bit stack stores complete register values temporarily. It also confirms that each PUSH decreases RSP by 8 bytes and each POP increases it by 8 bytes.
