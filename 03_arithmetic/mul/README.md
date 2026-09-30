# MUL Operations

## Program 1: mul1.asm

### Operation
The 8-bit unsigned multiplication produces:

250 = `0x00FA`

For 8-bit MUL:

AL × operand -> AX

The upper half of the result is AH = 0.

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Cleared (0) | The upper half of the result (AH) is zero. |
| OF | Cleared (0) | The upper half of the result (AH) is zero. |
| SF | Undefined | MUL does not define SF. |
| ZF | Undefined | MUL does not define ZF. |
| AF | Undefined | MUL does not define AF. |
| PF | Undefined | MUL does not define PF. |

Note: IF is not an arithmetic flag affected by MUL.

## Program 2: mul2.asm

### Operation
3000 × 200 = 600000

For 16-bit MUL:

AX × operand -> DX:AX

The result is:

`DX:AX = 0009:27C0`

Therefore DX = `0009` and AX = `27C0`.

### EFLAGS

| Flag | Status | Explanation |
|---|---|---|
| CF | Set (1) | The upper half of the result (DX) is non-zero (`0009`). |
| OF | Set (1) | The upper half of the result (DX) is non-zero (`0009`). |
| SF | Undefined | MUL does not define SF. |
| ZF | Undefined | MUL does not define ZF. |
| AF | Undefined | MUL does not define AF. |
| PF | Undefined | MUL does not define PF. |

For unsigned MUL, CF and OF are set when the upper half of the result is non-zero.
