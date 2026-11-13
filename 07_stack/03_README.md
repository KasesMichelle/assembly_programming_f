# 03.asm – CALL and RET Instructions

## 1. Introduction

This program demonstrates how CALL and RET use the stack to manage function calls and return addresses.

It also shows how a function can perform an operation and return the result to the calling program.

## 2. Program Execution Flow

**Step 1: Program Initialization**

Execution begins at `_start`.

`mov rax, 10` loads 10 into RAX.

**Step 2: Calling the Function**

`call calculate` transfers execution to the calculate function.

Before transferring control, CALL automatically pushes the address of the next instruction onto the stack.

This return address occupies 8 bytes, causing RSP to decrease by 8.

**Step 3: Function Execution**

Inside the calculate function:

`add rax, 5`

This adds 5 to the existing value in RAX.

Therefore:

RAX = 10 + 5 = 15.

The arithmetic operation does not change RSP.

**Step 4: Returning from the Function**

`ret` retrieves the saved return address from the top of the stack.

The processor uses this address to continue execution at `after_call`.

RSP increases by 8 bytes because the return address has been removed.

**Step 5: Continuing Execution**

The program reaches the `after_call` label.

At this point, RAX contains 15.

The `nop` instruction performs no operation.

**Step 6: Program Termination**

- `mov rax, 60` selects the Linux exit system call.
- `xor rdi, rdi` sets the exit status to zero.
- `syscall` terminates execution.

## 3. Stack Pointer Changes

Let the initial RSP be S.

| Instruction | RSP |
|---|---|
| Before CALL | S |
| CALL calculate | S - 8 |
| ADD RAX, 5 | S - 8 |
| RET | S |

CALL decreases RSP by 8 bytes because it pushes the return address. RET increases RSP by 8 bytes when retrieving it.

## 4. Observations

The program executes successfully with exit status 0.

No output appears on the terminal because the program does not contain output instructions.

The expected result is:
- Initial RAX = 10.
- Final calculation result = 15.
- RSP returns to its original value after RET.

The program demonstrates that CALL and RET automatically manage the return address using the stack.

## 5. Conclusion

This program illustrates the importance of the stack in function calls. CALL saves the return address, allowing the function to execute independently, while RET retrieves that address and resumes execution at the correct location.
