# ADD Operations

## Program 1: add1.asm

### Operation
120 + 10 = 130

The result is stored in an 8-bit register (AL).

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Cleared (0) | 130 fits within the unsigned 8-bit range (0–255), so there is no carry out. |
| OF | Set (1) | 120 + 10 = 130, which is greater than the signed 8-bit maximum of 127. |
| SF | Set (1) | The result 130 is `10000010` in binary, so the sign bit is 1. |
| ZF | Cleared (0) | The result is not zero. |
| AF | Set (1) | The lower nibble causes a carry from bit 3 to bit 4. |
| PF | Set (1) | `10000010` contains two 1-bits, giving even parity. |

Note: IF is not an arithmetic flag affected by ADD.

## Program 2: add2.asm

### Operation
32000 + 500 = 32500

The result is stored in a 16-bit register (AX).

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Cleared (0) | 32500 fits within the unsigned 16-bit range (0–65535). |
| OF | Cleared (0) | 32500 is within the signed 16-bit range (-32768 to 32767). |
| SF | Cleared (0) | The most significant bit of `0x7EF4` is 0. |
| ZF | Cleared (0) | The result is not zero. |
| AF | Cleared (0) | The lower nibble does not produce a carry. |
| PF | Cleared (0) | The low byte `F4` contains five 1-bits, giving odd parity. |

Note: IF is not an arithmetic flag affected by ADD.
