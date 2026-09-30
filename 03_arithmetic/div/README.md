# DIV Operations

## Program 1: div1.asm

### Operation
100 ÷ 7 = 14 remainder 2

For 8-bit DIV:

AX ÷ BL -> AL = quotient, AH = remainder

Therefore:
- AL = 14
- AH = 2
- AX = `020E`

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Undefined | DIV does not define CF. |
| OF | Undefined | DIV does not define OF. |
| SF | Undefined | DIV does not define SF. |
| ZF | Undefined | DIV does not define ZF. |
| AF | Undefined | DIV does not define AF. |
| PF | Undefined | DIV does not define PF. |

Note: The flags displayed by GDB after DIV should not be interpreted as being caused by the division.

## Program 2: div2.asm

### Operation
50000 ÷ 300 = 166 remainder 200

For 16-bit DIV:

DX:AX ÷ BX -> AX = quotient, DX = remainder

Before division:
- DX = 0
- AX = 50000
- BX = 300

After division:
- AX = 166
- DX = 200

Check:

300 × 166 + 200 = 50000

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Undefined | DIV does not define CF. |
| OF | Undefined | DIV does not define OF. |
| SF | Undefined | DIV does not define SF. |
| ZF | Undefined | DIV does not define ZF. |
| AF | Undefined | DIV does not define AF. |
| PF | Undefined | DIV does not define PF. |

Note: The flags displayed by GDB after DIV should not be interpreted as being caused by the division.
