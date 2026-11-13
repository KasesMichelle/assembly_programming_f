# 02.asm – Stack Frames and Local Variables

## 1. Introduction

This program demonstrates how a function uses the stack to create a stack frame, store local variables, and retrieve them. It uses RBP as a frame pointer and RSP as a stack pointer.

## 2. Program Execution Flow

**Step 1: Calling the Function**

Execution begins at `_start`.

- `call work` transfers execution to the work function.
- Before jumping, CALL automatically pushes the return address onto the stack.

Since this is a 64-bit program, RSP decreases by 8 bytes.

**Step 2: Saving the Previous Frame Pointer**

- `push rbp` saves the previous frame pointer onto the stack.
- RSP decreases by another 8 bytes.
- `mov rbp, rsp` establishes the new stack frame.

RBP now provides a stable reference point for accessing local variables.

**Step 3: Allocating Local Variables**

`sub rsp, 16` reserves 16 bytes of stack memory for two local variables.

RSP decreases by 16 bytes, while RBP remains unchanged.

**Step 4: Storing Values**

- `mov qword [rbp - 8], 100` stores 100 in the first local variable.
- `mov qword [rbp - 16], 200` stores 200 in the second local variable.

These instructions write directly into the allocated stack memory without changing RSP.

**Step 5: Retrieving Values**

- `mov rax, [rbp - 8]` retrieves 100 into RAX.
- `mov rbx, [rbp - 16]` retrieves 200 into RBX.

The values are accessed using offsets from RBP.

**Step 6: Restoring the Stack**

- `mov rsp, rbp` releases the allocated local-variable space.
- `pop rbp` restores the previous frame pointer.
- `ret` retrieves the return address and transfers execution back to `_start`.

Each operation restores the stack to its previous state.

**Step 7: Program Termination**

The program uses the Linux exit system call with status 0 to terminate execution.

## 3. Stack Pointer Changes

Let the initial RSP be S.

| Instruction | RSP |
|---|---|
| Before CALL | S |
| CALL work | S - 8 |
| PUSH RBP | S - 16 |
| MOV RBP, RSP | S - 16 |
| SUB RSP, 16 | S - 32 |
| MOV RSP, RBP | S - 16 |
| POP RBP | S - 8 |
| RET | S |

## 4. Observations

The program executes successfully with exit status 0 and produces no terminal output.

During execution:
- RAX receives 100.
- RBX receives 200.
- RBP remains the reference point for accessing local variables.
- RSP changes as memory is allocated and released.

After RET, execution returns to the calling section and the stack pointer is restored.

## 5. Conclusion

The program demonstrates how stack frames support function execution. It shows how local variables are allocated, accessed and removed while RBP provides a stable reference point.
