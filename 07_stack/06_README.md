# 06.asm – 32-bit Stack Operations

## 1. Introduction

This program demonstrates basic PUSH and POP operations using 32-bit registers.

It illustrates how values are stored on the stack, retrieved in reverse order and how ESP changes during these operations.

## 2. Program Execution Flow

**Step 1: Loading Values**

Execution begins at `_start`.

- `mov eax, 0x11223344` loads the hexadecimal value into EAX.
- `mov ebx, 0x1234` loads another value into EBX.

These instructions do not change ESP.

**Step 2: Pushing Values onto the Stack**

- `push eax` stores `0x11223344` on the stack.
- `push ebx` stores `0x1234` above the first value.

In 32-bit mode, each PUSH operation decreases ESP by 4 bytes.

The most recently pushed value becomes the topmost stack element.

**Step 3: NOP Instruction**

The `nop` instruction performs no operation. It allows the stack contents to be inspected before retrieving the values.

**Step 4: Popping Values**

- `pop ebx` retrieves `0x1234` into EBX.
- `pop eax` retrieves `0x11223344` into EAX.

Each POP increases ESP by 4 bytes.

The original register values are restored.

**Step 5: Program Termination**

- `mov eax, 1` selects the Linux 32-bit exit system call.
- `xor ebx, ebx` sets the exit status to zero.
- `int 0x80` invokes the system call and terminates the program.

## 3. Stack Pointer Changes

Let the initial ESP be S.

| Instruction | ESP |
|---|---|
| Initial state | S |
| PUSH EAX | S - 4 |
| PUSH EBX | S - 8 |
| POP EBX | S - 4 |
| POP EAX | S |

The stack pointer returns to its original value after all the values have been retrieved.

## 4. Observations

The program executes successfully with exit status 0.

It produces no terminal output because it does not contain printing instructions.

After execution:
- EAX contains `0x11223344`.
- EBX contains `0x1234` immediately after the POP operations.
- ESP returns to its original value.

The final instructions overwrite EAX and EBX to prepare for the exit system call.

The program demonstrates that 32-bit PUSH and POP operations use 4-byte stack increments.

## 5. Conclusion

This program demonstrates the LIFO behaviour of the stack using 32-bit registers. It shows how values are temporarily stored, retrieved and how ESP is adjusted during each operation.
