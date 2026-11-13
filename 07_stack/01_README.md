# 01.asm – Basic PUSH and POP Operations

## 1. Introduction
This program demonstrates basic stack operations using the PUSH and POP instructions. It illustrates how values are stored temporarily in the stack and retrieved using the Last In, First Out (LIFO) principle.

## 2. Program Execution Flow

**Step 1: Program Initialization**

Execution begins at `_start`.

- `mov rax, 100` loads the value 100 into RAX.
- `mov rbx, 200` loads the value 200 into RBX.

These instructions do not affect the stack pointer.

**Step 2: Pushing Values onto the Stack**

- `push rax` places 100 onto the stack.
- `push rbx` places 200 onto the stack.

In 64-bit mode, each PUSH operation decreases RSP by 8 bytes. The second value, 200, becomes the topmost stack element.

**Step 3: NOP Instruction**

The `nop` instruction performs no operation. It allows the program to reach a point where the stack contents can be inspected.

**Step 4: Popping Values from the Stack**

- `pop rcx` retrieves 200 into RCX.
- `pop rdx` retrieves 100 into RDX.

Each POP operation increases RSP by 8 bytes.

This demonstrates LIFO because the last value pushed is the first value retrieved.

**Step 5: Program Termination**

- `mov rax, 60` selects the Linux exit system call.
- `xor rdi, rdi` sets the exit status to zero.
- `syscall` terminates the program.

## 3. Stack Pointer Changes

Assuming the initial RSP is S:

| Instruction | RSP |
|---|---|
| Initial state | S |
| PUSH RAX | S - 8 |
| PUSH RBX | S - 16 |
| POP RCX | S - 8 |
| POP RDX | S |

The stack grows towards lower memory addresses during PUSH operations and moves towards higher addresses during POP operations.

## 4. Observations

The program executes successfully with exit status 0. It produces no terminal output because it does not contain any print instructions.

After execution:
- RCX contains 200.
- RDX contains 100.
- RSP returns to its original value.

## 5. Conclusion

The program demonstrates how PUSH and POP manipulate the stack. It confirms the LIFO principle and shows that every 64-bit PUSH or POP changes RSP by 8 bytes.
