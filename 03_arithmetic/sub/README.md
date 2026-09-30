# SUB Operations

## Program 1: sub1.asm

### Operation
50 - 80 = -30

The 8-bit two's complement representation of -30 is `E2`.

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Set (1) | 50 is less than 80 as unsigned values, so a borrow is required. |
| OF | Cleared (0) | The signed result -30 is within the signed 8-bit range. |
| SF | Set (1) | The result `E2` has its most significant bit set to 1. |
| ZF | Cleared (0) | The result is not zero. |
| AF | Cleared (0) | No borrow occurs from bit 4 in the lower nibble. |
| PF | Set (1) | `E2` contains four 1-bits, giving even parity. |

Note: GDB displays `E2` as unsigned 226, but its signed 8-bit interpretation is -30.

## Program 2: sub2.asm

### Operation
1000 - 2000 = -1000

The 16-bit two's complement representation of -1000 is `FC18`.

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Set (1) | 1000 is less than 2000 as unsigned values, so a borrow is required. |
| OF | Cleared (0) | The signed result -1000 is within the signed 16-bit range. |
| SF | Set (1) | `FC18` has its most significant bit set to 1. |
| ZF | Cleared (0) | The result is not zero. |
| AF | Cleared (0) | No borrow occurs from bit 4 in the lower nibble. |
| PF | Set (1) | The low byte `18` contains two 1-bits, giving even parity. |

Note: GDB displays `FC18` as unsigned 64536, but its signed 16-bit interpretation is -1000.
