# RISC-V P Extension intrinsics Documentation

## No Register-pair Packed SIMD intrinsics

### Packed Shift Left Immediate intrinsics

These intrinsics perform logical/arithmetic shift left operations with immediate shift amounts:

- pslli.* and psslai.* operate on packed elements (byte/half/word).

- sslai is a normal shift operation for RV32 only.

| Intrinsic | Signature | Availability |
|-----------|-----------|---------------|
| `__riscv_pslli_b` | `int8_t __riscv_pslli_b(int8_t rs1, int rs2);` | RV32/64 |
| `__riscv_pslli_h` | `int16_t __riscv_pslli_h(int16_t rs1, int rs2);` | RV32/64 |
| `__riscv_pslli_w` | `int32_t __riscv_pslli_w(int32_t rs1, int rs2);` | RV64 only |
| `__riscv_psslai_h` | `int16_t __riscv_psslai_h(int16_t rs1, int rs2);` | RV32/64 |
| `__riscv_psslai_w` | `int32_t __riscv_psslai_w(int32_t rs1, int rs2);` | RV64 only |
| `__riscv_sslai` | `int32_t __riscv_sslai(int32_t rs1, int rs2);` | RV32 only |

### Packed Immediate Load intrinsics

These intrinsics load a constant immediate value directly into a register:

- pli.b: Loads an 8-bit immediate into a byte element.

- pli.h: Loads a 16-bit immediate into a halfword element.

- pli.w: Loads a 32-bit immediate into a word element (only on RV64).

| Intrinsic         | Signature                                   | Availability |
|-------------------|---------------------------------------------|--------------|
| `__riscv_pli_b`   | `int8_t __riscv_pli_b(int imm);` | RV32/64      |
| `__riscv_pli_h`   | `int16_t __riscv_pli_h(int imm);` | RV32/64      |
| `__riscv_pli_w`   | `int32_t __riscv_pli_w(int imm);` | RV64 only    |


### Packed Sign Extension intrinsics

These intrinsics performs sign-extension of a smaller type to a larger one:

- psext.h.b: Sign-extends an 8-bit value to 16 bits.

- psext.w.b: Sign-extends an 8-bit value to 32 bits (RV64 only).

- psext.w.h: Sign-extends a 16-bit value to 32 bits (RV64 only).

| Intrinsic           | Signature                                  | Availability |
| ------------------- | ------------------------------------------ | ------------ |
| `__riscv_psext_h_b` | `int16_t __riscv_psext_h_b(int8_t rs1);`  | RV32/64      |
| `__riscv_psext_w_b` | `int32_t __riscv_psext_w_b(int8_t rs1);`  | RV64 only    |
| `__riscv_psext_w_h` | `int32_t __riscv_psext_w_h(int16_t rs1);` | RV64 only    |


### Packed Load Upper Immediate intrinsics

These intrinsics load an immediate value into the upper bits of a register:

- plui.h: Loads a 16-bit upper immediate into a halfword element.

- plui.w: Loads a 32-bit upper immediate into a word element (RV64 only).

| Intrinsic        | Signature                          | Availability |
| ---------------- | ---------------------------------- | ------------ |
| `__riscv_plui_h` | `int16_t __riscv_plui_h(int imm);` | RV32/64      |
| `__riscv_plui_w` | `int32_t __riscv_plui_w(int imm);` | RV64 only    |

### Packed Shift Left Register intrinsics

These intrinsics perform packed element-wise logical left shifts, where:

The second operand (rs2) provides the per-element shift amount.

Element widths are 8, 16, or 32 bits depending on the variant.

psll.ws is available only on RV64.

| Intrinsic         | Signature                                            | Availability |
| ----------------- | ---------------------------------------------------- | ------------ |
| `__riscv_psll_bs` | `int8_t __riscv_psll_bs(int8_t rs1, int8_t rs2);`    | RV32/64      |
| `__riscv_psll_hs` | `int16_t __riscv_psll_hs(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_psll_ws` | `int32_t __riscv_psll_ws(int32_t rs1, int32_t rs2);` | RV64 only    |

### Packed Addition intrinsics

These intrinsics perform packed signed addition on subword elements:

- padd.bs: Adds 8-bit elements in parallel.

- padd.hs: Adds 16-bit elements in parallel.

- padd.ws: Adds 32-bit elements in parallel (RV64 only).

| Intrinsic         | Signature                                            | Availability |
| ----------------- | ---------------------------------------------------- | ------------ |
| `__riscv_padd_bs` | `int8_t __riscv_padd_bs(int8_t rs1, int8_t rs2);`    | RV32/64      |
| `__riscv_padd_hs` | `int16_t __riscv_padd_hs(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_padd_ws` | `int32_t __riscv_padd_ws(int32_t rs1, int32_t rs2);` | RV64 only    |

### Packed Saturating Arithmetic Shift intrinsics

These intrinsics perform saturating arithmetic shift operations, with or without rounding:

- pssha.* and sha/ssha: Saturating left shifts.

- psshar.* and shar/sshar: Saturating right shifts (with rounding).

| Intrinsic           | Signature                                              | Availability |
| ------------------- | ------------------------------------------------------ | ------------ |
| `__riscv_pssha_hs`  | `int16_t __riscv_pssha_hs(int16_t rs1, int16_t rs2);`  | RV32/64      |
| `__riscv_pssha_ws`  | `int32_t __riscv_pssha_ws(int32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_sha`       | `int32_t __riscv_sha(int32_t rs1, int32_t rs2);`       | RV64 only    |
| `__riscv_ssha`      | `int32_t __riscv_ssha(int32_t rs1, int32_t rs2);`      | RV32 only    |
| `__riscv_psshar_hs` | `int16_t __riscv_psshar_hs(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_psshar_ws` | `int32_t __riscv_psshar_ws(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_shar`      | `int32_t __riscv_shar(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_sshar`     | `int32_t __riscv_sshar(int32_t rs1, int32_t rs2);`     | RV32 only    |

### Packed Shift Right Logical Immediate intrinsics

These intrinsics perform logical right shifts on packed data with an immediate shift amount:

psrli.b: 8-bit packed shift.

psrli.h: 16-bit packed shift.

psrli.w: 32-bit packed shift (RV64 only).

| Intrinsic         | Signature                                          | Availability |
| ----------------- | -------------------------------------------------- | ------------ |
| `__riscv_psrli_b` | `int8_t __riscv_psrli_b(int8_t rs1, int shamt);`   | RV32/64      |
| `__riscv_psrli_h` | `int16_t __riscv_psrli_h(int16_t rs1, int shamt);` | RV32/64      |
| `__riscv_psrli_w` | `int32_t __riscv_psrli_w(int32_t rs1, int shamt);` | RV64 only    |

### Packed Unsigned Saturating Immediate intrinsics

These intrinsics perform unsigned saturating operations with immediate limits:

- pusati.*: Operates on packed halfwords or words.

- usati: Normal unsigned saturate operation for RV32 and RV64.

| Intrinsic              | Signature                                           | Availability |
| ---------------------- | --------------------------------------------------- | ------------ |
| `__riscv_pusati_h`     | `uint16_t __riscv_pusati_h(uint16_t rs1, int imm);` | RV32/64      |
| `__riscv_pusati_w`     | `uint32_t __riscv_pusati_w(uint32_t rs1, int imm);` | RV64 only    |
| `__riscv_usati` (RV32) | `uint32_t __riscv_usati(uint32_t rs1, int imm);`    | RV32 only    |
| `__riscv_usati` (RV64) | `uint64_t __riscv_usati(uint64_t rs1, int imm);`    | RV64 only    |

### Packed Arithmetic Shift Right Immediate intrinsics

These intrinsics perform arithmetic right shifts with immediate values:

- psrai.*: Standard packed arithmetic right shift.

- psrari.*: Packed arithmetic right shift with rounding.

- srari: Normal arithmetic right shift for RV32 and RV64.

| Intrinsic              | Signature                                           | Availability |
| ---------------------- | --------------------------------------------------- | ------------ |
| `__riscv_psrai_b`      | `int8_t __riscv_psrai_b(int8_t rs1, int shamt);`    | RV32/64      |
| `__riscv_psrai_h`      | `int16_t __riscv_psrai_h(int16_t rs1, int shamt);`  | RV32/64      |
| `__riscv_psrai_w`      | `int32_t __riscv_psrai_w(int32_t rs1, int shamt);`  | RV64 only    |
| `__riscv_psrari_h`     | `int16_t __riscv_psrari_h(int16_t rs1, int shamt);` | RV32/64      |
| `__riscv_psrari_w`     | `int32_t __riscv_psrari_w(int32_t rs1, int shamt);` | RV64 only    |
| `__riscv_srari` (RV32) | `int32_t __riscv_srari(int32_t rs1, int shamt);`    | RV32 only    |
| `__riscv_srari` (RV64) | `int64_t __riscv_srari(int64_t rs1, int shamt);`    | RV64 only    |

### Packed Signed Saturating Immediate intrinsics

These intrinsics perform signed saturating operations with immediate limits:

- psati.*: Operates on packed halfwords or words.

- sati: Normal signed saturate operation for RV32 and RV64.

| Intrinsic             | Signature                                        | Availability |
| --------------------- | ------------------------------------------------ | ------------ |
| `__riscv_psati_h`     | `int16_t __riscv_psati_h(int16_t rs1, int imm);` | RV32/64      |
| `__riscv_psati_w`     | `int32_t __riscv_psati_w(int32_t rs1, int imm);` | RV64 only    |
| `__riscv_sati` (RV32) | `int32_t __riscv_sati(int32_t rs1, int imm);`    | RV32 only    |
| `__riscv_sati` (RV64) | `int64_t __riscv_sati(int64_t rs1, int imm);`    | RV64 only    |

### Packed Shift Right Logical Register intrinsics

These intrinsics perform packed element-wise logical right shifts, where:

The second operand (rs2) provides the per-element shift amount.

Element widths are 8, 16, or 32 bits depending on the variant.

psrl.ws is available only on RV64.

| Intrinsic         | Signature                                               | Availability |
| ----------------- | ------------------------------------------------------- | ------------ |
| `__riscv_psrl_bs` | `uint8_t __riscv_psrl_bs(uint8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_psrl_hs` | `uint16_t __riscv_psrl_hs(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_psrl_ws` | `uint32_t __riscv_psrl_ws(uint32_t rs1, uint32_t rs2);` | RV64 only    |

### Packed Predicated Summation intrinsics

These intrinsics compute predicated summations on packed signed and unsigned subwords:

predsum.* — signed predicated sum.

predsumu.* — unsigned predicated sum.

Available in byte, halfword, and word variants, with word variants for RV64 only.

| Intrinsic             | Signature                                                   | Availability |
| --------------------- | ----------------------------------------------------------- | ------------ |
| `__riscv_predsum_bs`  | `int8_t __riscv_predsum_bs(int8_t rs1, int8_t rs2);`        | RV32/64      |
| `__riscv_predsum_hs`  | `int16_t __riscv_predsum_hs(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_predsum_ws`  | `int32_t __riscv_predsum_ws(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_predsumu_bs` | `uint8_t __riscv_predsumu_bs(uint8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_predsumu_hs` | `uint16_t __riscv_predsumu_hs(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_predsumu_ws` | `uint32_t __riscv_predsumu_ws(uint32_t rs1, uint32_t rs2);` | RV64 only    |

### Packed Arithmetic Shift Right Register intrinsics

These intrinsics perform packed element-wise arithmetic right shifts, where:

The second operand (rs2) provides the per-element shift amount.

Element widths are 8, 16, or 32 bits depending on the variant.

psra.ws is available only on RV64.

| Intrinsic         | Signature                                            | Availability |
| ----------------- | ---------------------------------------------------- | ------------ |
| `__riscv_psra_bs` | `int8_t __riscv_psra_bs(int8_t rs1, int8_t rs2);`    | RV32/64      |
| `__riscv_psra_hs` | `int16_t __riscv_psra_hs(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_psra_ws` | `int32_t __riscv_psra_ws(int32_t rs1, int32_t rs2);` | RV64 only    |

### Packed Addition and Saturating Addition intrinsics

These intrinsics cover:

Packed signed and unsigned additions (padd.* / psadd.*, paddu.* / psaddu.*).

Saturating additions (sadd, aadd, saddu, aaddu).

Variants for bytes, halfwords, and words, with 64-bit availability for word size.

| Intrinsic          | Signature                                                | Availability |
| ------------------ | -------------------------------------------------------- | ------------ |
| `__riscv_padd_b`   | `int8_t __riscv_padd_b(int8_t rs1, int8_t rs2);`         | RV32/64      |
| `__riscv_padd_h`   | `int16_t __riscv_padd_h(int16_t rs1, int16_t rs2);`      | RV32/64      |
| `__riscv_padd_w`   | `int32_t __riscv_padd_w(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_sadd`     | `int32_t __riscv_sadd(int32_t rs1, int32_t rs2);`        | RV32 only    |
| `__riscv_psadd_b`  | `int8_t __riscv_psadd_b(int8_t rs1, int8_t rs2);`        | RV32/64      |
| `__riscv_psadd_h`  | `int16_t __riscv_psadd_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_psadd_w`  | `int32_t __riscv_psadd_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_aadd`     | `int32_t __riscv_aadd(int32_t rs1, int32_t rs2);`        | RV32 only    |
| `__riscv_paadd_b`  | `int8_t __riscv_paadd_b(int8_t rs1, int8_t rs2);`        | RV32/64      |
| `__riscv_paadd_h`  | `int16_t __riscv_paadd_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_paadd_w`  | `int32_t __riscv_paadd_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_saddu`    | `uint32_t __riscv_saddu(uint32_t rs1, uint32_t rs2);`    | RV32 only    |
| `__riscv_psaddu_b` | `uint8_t __riscv_psaddu_b(uint8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_psaddu_h` | `uint16_t __riscv_psaddu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_psaddu_w` | `uint32_t __riscv_psaddu_w(uint32_t rs1, uint32_t rs2);` | RV64 only    |
| `__riscv_aaddu`    | `uint32_t __riscv_aaddu(uint32_t rs1, uint32_t rs2);`    | RV32 only    |
| `__riscv_paaddu_b` | `uint8_t __riscv_paaddu_b(uint8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_paaddu_h` | `uint16_t __riscv_paaddu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_paaddu_w` | `uint32_t __riscv_paaddu_w(uint32_t rs1, uint32_t rs2);` | RV64 only    |

### Packed Subtraction and Saturating Subtraction intrinsics

These intrinsics perform subtraction on packed data types with the following behaviors:

- psub.* variants perform element-wise signed subtraction.

- pssub.* variants perform element-wise signed saturating subtraction, clamping to the signed range of the element size.

- ssub/asub perform normal saturating subtraction for 32-bit values on RV32.

- pasub.* variants perform element-wise unsigned subtraction.

- pssubu.* variants perform element-wise unsigned saturating subtraction, clamping to the unsigned range.

- ssubu/asubu perform normal unsigned saturating subtraction for 32-bit values on RV32.

| Intrinsic          | Signature                                                | Availability |
| ------------------ | -------------------------------------------------------- | ------------ |
| `__riscv_psub_b`   | `int8_t  __riscv_psub_b(int8_t rs1, int8_t rs2);`        | RV32/64      |
| `__riscv_psub_h`   | `int16_t __riscv_psub_h(int16_t rs1, int16_t rs2);`      | RV32/64      |
| `__riscv_psub_w`   | `int32_t __riscv_psub_w(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_ssub`     | `int32_t __riscv_ssub(int32_t rs1, int32_t rs2);`        | RV32 only    |
| `__riscv_pssub_b`  | `int8_t  __riscv_pssub_b(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pssub_h`  | `int16_t __riscv_pssub_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pssub_w`  | `int32_t __riscv_pssub_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_asub`     | `int32_t __riscv_asub(int32_t rs1, int32_t rs2);`        | RV32 only    |
| `__riscv_pasub_b`  | `int8_t  __riscv_pasub_b(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pasub_h`  | `int16_t __riscv_pasub_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pasub_w`  | `int32_t __riscv_pasub_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_ssubu`    | `uint32_t __riscv_ssubu(uint32_t rs1, uint32_t rs2);`    | RV32 only    |
| `__riscv_pssubu_b` | `uint8_t  __riscv_pssubu_b(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pssubu_h` | `uint16_t __riscv_pssubu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_pssubu_w` | `uint32_t __riscv_pssubu_w(uint32_t rs1, uint32_t rs2);` | RV64 only    |
| `__riscv_asubu`    | `uint32_t __riscv_asubu(uint32_t rs1, uint32_t rs2);`    | RV32 only    |
| `__riscv_pasubu_b` | `uint8_t  __riscv_pasubu_b(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pasubu_h` | `uint16_t __riscv_pasubu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_pasubu_w` | `uint32_t __riscv_pasubu_w(uint32_t rs1, uint32_t rs2);` | RV64 only    |

### Packed Difference intrinsics

These intrinsics compute the element-wise absolute difference between packed elements:

pdif.* variants perform signed absolute difference on 8-bit and 16-bit elements.

pdifu.* variants perform unsigned absolute difference on 8-bit and 16-bit elements.

| Intrinsic         | Signature                                               | Availability |
| ----------------- | ------------------------------------------------------- | ------------ |
| `__riscv_pdif_b`  | `int8_t  __riscv_pdif_b(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pdif_h`  | `int16_t __riscv_pdif_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pdifu_b` | `uint8_t  __riscv_pdifu_b(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pdifu_h` | `uint16_t __riscv_pdifu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |

### Packed Shift Left and Shift Right intrinsics

This intrinsic performs an element-wise packed left/right shift, where:

Each element in rs1 is shifted left/right by the corresponding element in rs2.

| Intrinsic     | Signature                                        | Availability |
| ------------- | ------------------------------------------------ | ------------ |
| `__riscv_slx` | `int32_t __riscv_slx(int32_t rs1, int32_t rs2);` | RV32/64      |
| `__riscv_srx` | `int32_t __riscv_srx(int32_t rs1, int32_t rs2);` | RV32/64      |

### Packed Multiplication intrinsics

These intrinsics perform packed multiplication on elements of specified widths, signed or unsigned variants.

| Intrinsic             | Signature                                                   | Availability |
| --------------------- | ----------------------------------------------------------- | ------------ |
| `__riscv_pmul_h_b01`  | `int16_t __riscv_pmul_h_b01(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pmul_w_h01`  | `int32_t __riscv_pmul_w_h01(int16_t rs1, int16_t rs2);`     | RV64 only    |
| `__riscv_pmulu_h_b01` | `uint16_t __riscv_pmulu_h_b01(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pmulu_w_h01` | `uint32_t __riscv_pmulu_w_h01(uint16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_mul_h01`     | `int16_t __riscv_mul_h01(int16_t rs1, int16_t rs2);`        | RV32 only    |
| `__riscv_mul_w01`     | `int32_t __riscv_mul_w01(int32_t rs1, int32_t rs2);`        | RV64 only    |
| `__riscv_mulu_h01`    | `uint16_t __riscv_mulu_h01(uint16_t rs1, uint16_t rs2);`    | RV32 only    |
| `__riscv_mulu_w01`    | `uint32_t __riscv_mulu_w01(uint32_t rs1, uint32_t rs2);`    | RV64 only    |

### Packed Multiply-Accumulate intrinsics

These intrinsics perform packed multiply-accumulate operations:

Multiply elements from two vectors and accumulate the results into a destination.

| Intrinsic              | Signature                                                                  | Availability |
| ---------------------- | -------------------------------------------------------------------------- | ------------ |
| `__riscv_pmacc_w_h01`  | `int32_t __riscv_pmacc_w_h01(int16_t rs1, int16_t rs2, int32_t acc);`      | RV64 only    |
| `__riscv_pmaccu_w_h01` | `uint32_t __riscv_pmaccu_w_h01(uint16_t rs1, uint16_t rs2, uint32_t acc);` | RV64 only    |
| `__riscv_macc_h01`     | `int16_t __riscv_macc_h01(int16_t rs1, int16_t rs2, int16_t acc);`         | RV32 only    |
| `__riscv_macc_w01`     | `int32_t __riscv_macc_w01(int32_t rs1, int32_t rs2, int32_t acc);`         | RV64 only    |
| `__riscv_maccu_h01`    | `uint16_t __riscv_maccu_h01(uint16_t rs1, uint16_t rs2, uint16_t acc);`    | RV32 only    |
| `__riscv_maccu_w01`    | `uint32_t __riscv_maccu_w01(uint32_t rs1, uint32_t rs2, uint32_t acc);`    | RV64 only    |

### Packed Vector Move and Merge intrinsics

These intrinsics perform vector move and merge operations:

- mvm and mvmn perform vector move operations with slight variations.

- merge combines elements from two vectors based on a mask or condition.

| Intrinsic       | Signature                                       | Availability |
| --------------- | ----------------------------------------------- | ------------ |
| `__riscv_mvm`   | `int __riscv_mvm(int rs1, int rs2, int rs3);`   | RV32/64      |
| `__riscv_mvmn`  | `int __riscv_mvmn(int rs1, int rs2, int rs3);`  | RV32/64      |
| `__riscv_merge` | `int __riscv_merge(int rs1, int rs2, int rs3);` | RV32/64      |

### Packed Difference and Summation intrinsics

These intrinsics compute packed element-wise difference followed by summation with unsigned saturation:

- pdifsumu.b computes the difference and sums unsigned bytes with saturation.

- pdifsumau.b is a variant with additional accumulation behavior.

| Intrinsic             | Signature                                                             | Availability |
| --------------------- | --------------------------------------------------------------------- | ------------ |
| `__riscv_pdifsumu_b`  | `uint8_t __riscv_pdifsumu_b(uint8_t rs1, uint8_t rs2, uint8_t rs3);`  | RV32/64      |
| `__riscv_pdifsumau_b` | `uint8_t __riscv_pdifsumau_b(uint8_t rs1, uint8_t rs2, uint8_t rs3);` | RV32/64      |

### Packed Shift-and-Add (SH1ADD) Intrinsics

These intrinsics perform a "shift-left-by-1 then add" operation on each packed element:

- psh1add.* does a basic left shift by 1 followed by addition.

- pssh1sadd.* performs the same with saturation.

- ssh1sadd is a normal version for RV32 saturation shift-add.

| Intrinsic             | Signature                                                | Availability |
| --------------------- | -------------------------------------------------------- | ------------ |
| `__riscv_psh1add_h`   | `int16_t __riscv_psh1add_h(int16_t rs1, int16_t rs2);`   | RV32/64      |
| `__riscv_psh1add_w`   | `int32_t __riscv_psh1add_w(int32_t rs1, int32_t rs2);`   | RV64 only    |
| `__riscv_ssh1sadd`    | `int32_t __riscv_ssh1sadd(int32_t rs1, int32_t rs2);`    | RV32 only    |
| `__riscv_pssh1sadd_h` | `int16_t __riscv_pssh1sadd_h(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_pssh1sadd_w` | `int32_t __riscv_pssh1sadd_w(int32_t rs1, int32_t rs2);` | RV64 only    |

### Packed Zip and Unzip Intrinsics

These instructions perform element-wise interleaving (zip) or deinterleaving (unzip) on 8-bit or 16-bit packed elements:

- zip* operations merge alternating elements from two source registers into one.

- unzip* operations separate interleaved elements from a packed register.

The hp variants operate on high-positioned packed elements (e.g., upper halves).

| Intrinsic           | Signature                                              | Availability |
| ------------------- | ------------------------------------------------------ | ------------ |
| `__riscv_unzip8p`   | `int64_t __riscv_unzip8p(int64_t rs1, int64_t rs2);`   | RV64 only    |
| `__riscv_unzip16p`  | `int64_t __riscv_unzip16p(int64_t rs1, int64_t rs2);`  | RV64 only    |
| `__riscv_unzip8hp`  | `int64_t __riscv_unzip8hp(int64_t rs1, int64_t rs2);`  | RV64 only    |
| `__riscv_unzip16hp` | `int64_t __riscv_unzip16hp(int64_t rs1, int64_t rs2);` | RV64 only    |
| `__riscv_zip8p`     | `int64_t __riscv_zip8p(int64_t rs1, int64_t rs2);`     | RV64 only    |
| `__riscv_zip16p`    | `int64_t __riscv_zip16p(int64_t rs1, int64_t rs2);`    | RV64 only    |
| `__riscv_zip8hp`    | `int64_t __riscv_zip8hp(int64_t rs1, int64_t rs2);`    | RV64 only    |
| `__riscv_zip16hp`   | `int64_t __riscv_zip16hp(int64_t rs1, int64_t rs2);`   | RV64 only    |

### Packed Multiply Intrinsics (Lane Variants 00 and 11)

These packed multiply instructions perform element-wise multiplication with signed, unsigned, or mixed signed/unsigned operands:

.b00, .b11, .h00, .h11 specify the byte/halfword lane positions.

- pmul* variants are vectorized forms of normal mul*, operating on sub-words.

- pmulsu* variants handle signed-unsigned mixed multiplication.

Useful in image, DSP, and cryptographic processing with tight data packing.

| Intrinsic              | Signature                                                   | Availability |
| ---------------------- | ----------------------------------------------------------- | ------------ |
| `__riscv_pmul_h_b00`   | `int16_t __riscv_pmul_h_b00(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pmul_w_h00`   | `int32_t __riscv_pmul_w_h00(int16_t rs1, int16_t rs2);`     | RV64 only    |
| `__riscv_pmul_h_b11`   | `int16_t __riscv_pmul_h_b11(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pmul_w_h11`   | `int32_t __riscv_pmul_w_h11(int16_t rs1, int16_t rs2);`     | RV64 only    |
| `__riscv_pmulu_h_b00`  | `uint16_t __riscv_pmulu_h_b00(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pmulu_w_h00`  | `uint32_t __riscv_pmulu_w_h00(uint16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_pmulu_h_b11`  | `uint16_t __riscv_pmulu_h_b11(uint8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pmulu_w_h11`  | `uint32_t __riscv_pmulu_w_h11(uint16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_pmulsu_h_b00` | `int16_t __riscv_pmulsu_h_b00(int8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_pmulsu_w_h00` | `int32_t __riscv_pmulsu_w_h00(int16_t rs1, uint16_t rs2);`  | RV64 only    |
| `__riscv_pmulsu_h_b11` | `int16_t __riscv_pmulsu_h_b11(int8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_pmulsu_w_h11` | `int32_t __riscv_pmulsu_w_h11(int16_t rs1, uint16_t rs2);`  | RV64 only    |
| `__riscv_mul_h00`      | `int16_t __riscv_mul_h00(int8_t rs1, int8_t rs2);`          | RV32         |
| `__riscv_mul_w00`      | `int32_t __riscv_mul_w00(int16_t rs1, int16_t rs2);`        | RV64 only    |
| `__riscv_mul_h11`      | `int16_t __riscv_mul_h11(int8_t rs1, int8_t rs2);`          | RV32         |
| `__riscv_mul_w11`      | `int32_t __riscv_mul_w11(int16_t rs1, int16_t rs2);`        | RV64 only    |
| `__riscv_mulu_h00`     | `uint16_t __riscv_mulu_h00(uint8_t rs1, uint8_t rs2);`      | RV32         |
| `__riscv_mulu_w00`     | `uint32_t __riscv_mulu_w00(uint16_t rs1, uint16_t rs2);`    | RV64 only    |
| `__riscv_mulu_h11`     | `uint16_t __riscv_mulu_h11(uint8_t rs1, uint8_t rs2);`      | RV32         |
| `__riscv_mulu_w11`     | `uint32_t __riscv_mulu_w11(uint16_t rs1, uint16_t rs2);`    | RV64 only    |
| `__riscv_mulsu_h00`    | `int16_t __riscv_mulsu_h00(int8_t rs1, uint8_t rs2);`       | RV32         |
| `__riscv_mulsu_w00`    | `int32_t __riscv_mulsu_w00(int16_t rs1, uint16_t rs2);`     | RV64 only    |
| `__riscv_mulsu_h11`    | `int16_t __riscv_mulsu_h11(int8_t rs1, uint8_t rs2);`       | RV32         |
| `__riscv_mulsu_w11`    | `int32_t __riscv_mulsu_w11(int16_t rs1, uint16_t rs2);`     | RV64 only    |

### Packed and Reordered Pack Intrinsics

These packed and reordered pack instructions support different byte/halfword ordering schemes when combining two registers into a single packed word:

- ppack combines elements straightforwardly.

- ppackbt and ppacktb reorder the byte lanes:

- bt: "byte-top" – high bytes from rs1, low bytes from rs2.

- tb: "top-byte" – reverse of bt.

- ppackt and packt interleave elements in an alternating pattern.

The normal versions (packbt, packtb, packt) offer the same behavior for word-level operations.

| Intrinsic           | Signature                                              | Availability |
| ------------------- | ------------------------------------------------------ | ------------ |
| `__riscv_ppack_h`   | `int16_t __riscv_ppack_h(int16_t rs1, int16_t rs2);`   | RV32/64      |
| `__riscv_ppack_w`   | `int32_t __riscv_ppack_w(int32_t rs1, int32_t rs2);`   | RV64 only    |
| `__riscv_ppackbt_h` | `int16_t __riscv_ppackbt_h(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_ppackbt_w` | `int32_t __riscv_ppackbt_w(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_packbt`    | `int32_t __riscv_packbt(int32_t rs1, int32_t rs2);`    | RV32/64      |
| `__riscv_ppacktb_h` | `int16_t __riscv_ppacktb_h(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_ppacktb_w` | `int32_t __riscv_ppacktb_w(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_packtb`    | `int32_t __riscv_packtb(int32_t rs1, int32_t rs2);`    | RV32/64      |
| `__riscv_ppackt_h`  | `int16_t __riscv_ppackt_h(int16_t rs1, int16_t rs2);`  | RV32/64      |
| `__riscv_ppackt_w`  | `int32_t __riscv_ppackt_w(int32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_packt`     | `int32_t __riscv_packt(int32_t rs1, int32_t rs2);`     | RV32/64      |

### Packed Multiply-Add and Multiply-Add-Accumulate Intrinsics

These intrinsics implement packed multiply-add, multiply-add accumulate, subtract, and saturating variants,

supporting various element widths (byte, halfword, word) and signed/unsigned variants. 

They are heavily used in vectorized DSP and signal processing to perform element-wise multiply-accumulate operations efficiently.

| Intrinsic               | Signature                                                  | Availability |
| ----------------------- | ---------------------------------------------------------- | ------------ |
| `__riscv_pm2add_h`      | `int16_t __riscv_pm2add_h(int16_t rs1, int16_t rs2);`      | RV32/64      |
| `__riscv_pm2add_w`      | `int32_t __riscv_pm2add_w(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_pm4add_b`      | `int8_t __riscv_pm4add_b(int8_t rs1, int8_t rs2);`         | RV32/64      |
| `__riscv_pm4add_h`      | `int16_t __riscv_pm4add_h(int16_t rs1, int16_t rs2);`      | RV64 only    |
| `__riscv_pm2adda_h`     | `int16_t __riscv_pm2adda_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pm2adda_w`     | `int32_t __riscv_pm2adda_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_pm4adda_b`     | `int8_t __riscv_pm4adda_b(int8_t rs1, int8_t rs2);`        | RV32/64      |
| `__riscv_pm4adda_h`     | `int16_t __riscv_pm4adda_h(int16_t rs1, int16_t rs2);`     | RV64 only    |
| `__riscv_pm2add_hx`     | `int16_t __riscv_pm2add_hx(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pm2add_wx`     | `int32_t __riscv_pm2add_wx(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_pm2adda_hx`    | `int16_t __riscv_pm2adda_hx(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pm2adda_wx`    | `int32_t __riscv_pm2adda_wx(int32_t rs1, int32_t rs2);`    | RV64 only    |
| `__riscv_pm2addu_h`     | `uint16_t __riscv_pm2addu_h(uint16_t rs1, uint16_t rs2);`  | RV32/64      |
| `__riscv_pm2addu_w`     | `uint32_t __riscv_pm2addu_w(uint32_t rs1, uint32_t rs2);`  | RV64 only    |
| `__riscv_pm4addu_b`     | `uint8_t __riscv_pm4addu_b(uint8_t rs1, uint8_t rs2);`     | RV32/64      |
| `__riscv_pm4addu_h`     | `uint16_t __riscv_pm4addu_h(uint16_t rs1, uint16_t rs2);`  | RV64 only    |
| `__riscv_pm2addau_h`    | `uint16_t __riscv_pm2addau_h(uint16_t rs1, uint16_t rs2);` | RV32/64      |
| `__riscv_pm2addau_w`    | `uint32_t __riscv_pm2addau_w(uint32_t rs1, uint32_t rs2);` | RV64 only    |
| `__riscv_pm4addau_b`    | `uint8_t __riscv_pm4addau_b(uint8_t rs1, uint8_t rs2);`    | RV32/64      |
| `__riscv_pm4addau_h`    | `uint16_t __riscv_pm4addau_h(uint16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_pmq2add_h`     | `int16_t __riscv_pmq2add_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pmq2add_w`     | `int32_t __riscv_pmq2add_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_pmqr2add_h`    | `int16_t __riscv_pmqr2add_h(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pmqr2add_w`    | `int32_t __riscv_pmqr2add_w(int32_t rs1, int32_t rs2);`    | RV64 only    |
| `__riscv_pmq2adda_h`    | `int16_t __riscv_pmq2adda_h(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pmq2adda_w`    | `int32_t __riscv_pmq2adda_w(int32_t rs1, int32_t rs2);`    | RV64 only    |
| `__riscv_pmqr2adda_h`   | `int16_t __riscv_pmqr2adda_h(int16_t rs1, int16_t rs2);`   | RV32/64      |
| `__riscv_pmqr2adda_w`   | `int32_t __riscv_pmqr2adda_w(int32_t rs1, int32_t rs2);`   | RV64 only    |
| `__riscv_pm2sub_h`      | `int16_t __riscv_pm2sub_h(int16_t rs1, int16_t rs2);`      | RV32/64      |
| `__riscv_pm2sub_w`      | `int32_t __riscv_pm2sub_w(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_pm2sadd_h`     | `int16_t __riscv_pm2sadd_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pm2suba_h`     | `int16_t __riscv_pm2suba_h(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pm2suba_w`     | `int32_t __riscv_pm2suba_w(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_pm2sub_hx`     | `int16_t __riscv_pm2sub_hx(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_pm2sub_wx`     | `int32_t __riscv_pm2sub_wx(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_pm2sadd_hx`    | `int16_t __riscv_pm2sadd_hx(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pm2suba_hx`    | `int16_t __riscv_pm2suba_hx(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pm2suba_wx`    | `int32_t __riscv_pm2suba_wx(int32_t rs1, int32_t rs2);`    | RV64 only    |
| `__riscv_pm2addsu_h`    | `int16_t __riscv_pm2addsu_h(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_pm2addsu_w`    | `int32_t __riscv_pm2addsu_w(int32_t rs1, int32_t rs2);`    | RV64 only    |
| `__riscv_pm4addsu_b`    | `int8_t __riscv_pm4addsu_b(int8_t rs1, int8_t rs2);`       | RV32/64      |
| `__riscv_pm4addsu_h`    | `int16_t __riscv_pm4addsu_h(int16_t rs1, int16_t rs2);`    | RV64 only    |
| `__riscv_pm2addasu_h`   | `int16_t __riscv_pm2addasu_h(int16_t rs1, int16_t rs2);`   | RV32/64      |
| `__riscv_pm2addasu_w`   | `int32_t __riscv_pm2addasu_w(int32_t rs1, int32_t rs2);`   | RV64 only    |
| `__riscv_pm4addasu_b`   | `int8_t __riscv_pm4addasu_b(int8_t rs1, int8_t rs2);`      | RV32/64      |
| `__riscv_pm4addasu_h`   | `int16_t __riscv_pm4addasu_h(int16_t rs1, int16_t rs2);`   | RV64 only    |
| `__riscv_pmqacc_w_h01`  | `int32_t __riscv_pmqacc_w_h01(int32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_pmqracc_w_h01` | `int32_t __riscv_pmqracc_w_h01(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_mqacc_h01`     | `int16_t __riscv_mqacc_h01(int16_t rs1, int16_t rs2);`     | RV32/64      |
| `__riscv_mqacc_w01`     | `int32_t __riscv_mqacc_w01(int32_t rs1, int32_t rs2);`     | RV64 only    |
| `__riscv_mqracc_h01`    | `int16_t __riscv_mqracc_h01(int16_t rs1, int16_t rs2);`    | RV32/64      |
| `__riscv_mqracc_w01`    | `int32_t __riscv_mqracc_w01(int32_t rs1, int32_t rs2);`    | RV64 only    |

### Cross-Lane Packed Add/Sub Intrinsics

These intrinsics handle cross-lane arithmetic on packed data:

- pas / psa: cross-lane addition (standard or saturating).

- pssa: cross-lane subtract with saturation.

- paas / pasa: weighted cross-lane add/sub (saturating).

Suffix .hx operates on 16-bit lanes; .wx on 32-bit lanes.

| Intrinsic         | Signature                                            | Availability |
| ----------------- | ---------------------------------------------------- | ------------ |
| `__riscv_pas_hx`  | `int16_t __riscv_pas_hx(int16_t rs1, int16_t rs2);`  | RV32/64      |
| `__riscv_pas_wx`  | `int32_t __riscv_pas_wx(int32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_psa_hx`  | `int16_t __riscv_psa_hx(int16_t rs1, int16_t rs2);`  | RV32/64      |
| `__riscv_psa_wx`  | `int32_t __riscv_psa_wx(int32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_psas_hx` | `int16_t __riscv_psas_hx(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_psas_wx` | `int32_t __riscv_psas_wx(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_pssa_hx` | `int16_t __riscv_pssa_hx(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_pssa_wx` | `int32_t __riscv_pssa_wx(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_paas_hx` | `int16_t __riscv_paas_hx(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_paas_wx` | `int32_t __riscv_paas_wx(int32_t rs1, int32_t rs2);` | RV64 only    |
| `__riscv_pasa_hx` | `int16_t __riscv_pasa_hx(int16_t rs1, int16_t rs2);` | RV32/64      |
| `__riscv_pasa_wx` | `int32_t __riscv_pasa_wx(int32_t rs1, int32_t rs2);` | RV64 only    |

### Packed Comparison and Min/Max Intrinsics

These intrinsics perform element-wise comparison operations on packed vectors or normal registers, producing masks or selection results. The operations include:

Equality comparison (mseq, pmseq.*)

Signed and unsigned less-than comparison (mslt, pmslt.*, msltu, pmsltu.*)

Element-wise minimum and maximum (pmin.*, pminu.*, pmax.*, pmaxu.*)

| Intrinsic          | Signature                                                | Availability | Description                        |
| ------------------ | -------------------------------------------------------- | ------------ | ---------------------------------- |
| `__riscv_mseq`     | `int32_t __riscv_mseq(int32_t rs1, int32_t rs2);`        | RV32 only    | Normal equality comparison         |
| `__riscv_pmseq_b`  | `int8_t __riscv_pmseq_b(int8_t rs1, int8_t rs2);`        | RV32/64      | Packed equality compare (8-bit)    |
| `__riscv_pmseq_h`  | `int16_t __riscv_pmseq_h(int16_t rs1, int16_t rs2);`     | RV32/64      | Packed equality compare (16-bit)   |
| `__riscv_pmseq_w`  | `int32_t __riscv_pmseq_w(int32_t rs1, int32_t rs2);`     | RV64 only    | Packed equality compare (32-bit)   |
| `__riscv_mslt`     | `int32_t __riscv_mslt(int32_t rs1, int32_t rs2);`        | RV32 only    | Normal signed less-than compare    |
| `__riscv_pmslt_b`  | `int8_t __riscv_pmslt_b(int8_t rs1, int8_t rs2);`        | RV32/64      | Packed signed less-than (8-bit)    |
| `__riscv_pmslt_h`  | `int16_t __riscv_pmslt_h(int16_t rs1, int16_t rs2);`     | RV32/64      | Packed signed less-than (16-bit)   |
| `__riscv_pmslt_w`  | `int32_t __riscv_pmslt_w(int32_t rs1, int32_t rs2);`     | RV64 only    | Packed signed less-than (32-bit)   |
| `__riscv_msltu`    | `uint32_t __riscv_msltu(uint32_t rs1, uint32_t rs2);`    | RV32 only    | Normal unsigned less-than compare  |
| `__riscv_pmsltu_b` | `uint8_t __riscv_pmsltu_b(uint8_t rs1, uint8_t rs2);`    | RV32/64      | Packed unsigned less-than (8-bit)  |
| `__riscv_pmsltu_h` | `uint16_t __riscv_pmsltu_h(uint16_t rs1, uint16_t rs2);` | RV32/64      | Packed unsigned less-than (16-bit) |
| `__riscv_pmsltu_w` | `uint32_t __riscv_pmsltu_w(uint32_t rs1, uint32_t rs2);` | RV64 only    | Packed unsigned less-than (32-bit) |
| `__riscv_pmin_b`   | `int8_t __riscv_pmin_b(int8_t rs1, int8_t rs2);`         | RV32/64      | Packed signed minimum (8-bit)      |
| `__riscv_pmin_h`   | `int16_t __riscv_pmin_h(int16_t rs1, int16_t rs2);`      | RV32/64      | Packed signed minimum (16-bit)     |
| `__riscv_pmin_w`   | `int32_t __riscv_pmin_w(int32_t rs1, int32_t rs2);`      | RV64 only    | Packed signed minimum (32-bit)     |
| `__riscv_pminu_b`  | `uint8_t __riscv_pminu_b(uint8_t rs1, uint8_t rs2);`     | RV32/64      | Packed unsigned minimum (8-bit)    |
| `__riscv_pminu_h`  | `uint16_t __riscv_pminu_h(uint16_t rs1, uint16_t rs2);`  | RV32/64      | Packed unsigned minimum (16-bit)   |
| `__riscv_pminu_w`  | `uint32_t __riscv_pminu_w(uint32_t rs1, uint32_t rs2);`  | RV64 only    | Packed unsigned minimum (32-bit)   |
| `__riscv_pmax_b`   | `int8_t __riscv_pmax_b(int8_t rs1, int8_t rs2);`         | RV32/64      | Packed signed maximum (8-bit)      |
| `__riscv_pmax_h`   | `int16_t __riscv_pmax_h(int16_t rs1, int16_t rs2);`      | RV32/64      | Packed signed maximum (16-bit)     |
| `__riscv_pmax_w`   | `int32_t __riscv_pmax_w(int32_t rs1, int32_t rs2);`      | RV64 only    | Packed signed maximum (32-bit)     |
| `__riscv_pmaxu_b`  | `uint8_t __riscv_pmaxu_b(uint8_t rs1, uint8_t rs2);`     | RV32/64      | Packed unsigned maximum (8-bit)    |
| `__riscv_pmaxu_h`  | `uint16_t __riscv_pmaxu_h(uint16_t rs1, uint16_t rs2);`  | RV32/64      | Packed unsigned maximum (16-bit)   |
| `__riscv_pmaxu_w`  | `uint32_t __riscv_pmaxu_w(uint32_t rs1, uint32_t rs2);`  | RV64 only    | Packed unsigned maximum (32-bit)   |

### Packed High-half Multiply and Accumulate Intrinsics

These intrinsics compute the high half (upper bits) or rounded high half of the product for signed, unsigned, and mixed operand variants, with optional lane selection:

- pmulh* / pmulhu*: high half of signed/unsigned multiplications.

- pmulhr* / pmulhru*: rounded high half variants.

- pmulhsu*, pmulhrsu*: signed–unsigned mixed high half.

Lane suffixes (.b0, .b1, .h0, .h1) select which elements are multiplied within packed registers.

Normal mulh*, mulhr*, and mulhrsu handle word-level operations on RV32.

| Intrinsic              | Signature                                                  | Availability |
| ---------------------- | ---------------------------------------------------------- | ------------ |
| `__riscv_pmulh_h`      | `int16_t __riscv_pmulh_h(int16_t rs1, int16_t rs2);`       | RV32/64      |
| `__riscv_pmulh_w`      | `int32_t __riscv_pmulh_w(int32_t rs1, int32_t rs2);`       | RV64 only    |
| `__riscv_pmulh_h_b0`   | `int16_t __riscv_pmulh_h_b0(int8_t rs1, int8_t rs2);`      | RV32/64      |
| `__riscv_pmulh_w_h0`   | `int32_t __riscv_pmulh_w_h0(int16_t rs1, int16_t rs2);`    | RV64 only    |
| `__riscv_pmulh_h_b1`   | `int16_t __riscv_pmulh_h_b1(int8_t rs1, int8_t rs2);`      | RV32/64      |
| `__riscv_pmulh_w_h1`   | `int32_t __riscv_pmulh_w_h1(int16_t rs1, int16_t rs2);`    | RV64 only    |
| `__riscv_pmulhu_h`     | `uint16_t __riscv_pmulhu_h(uint16_t rs1, uint16_t rs2);`   | RV32/64      |
| `__riscv_pmulhu_w`     | `uint32_t __riscv_pmulhu_w(uint32_t rs1, uint32_t rs2);`   | RV64 only    |
| `__riscv_pmulhr_h`     | `int16_t __riscv_pmulhr_h(int16_t rs1, int16_t rs2);`      | RV32/64      |
| `__riscv_pmulhr_w`     | `int32_t __riscv_pmulhr_w(int32_t rs1, int32_t rs2);`      | RV64 only    |
| `__riscv_pmulhru_h`    | `uint16_t __riscv_pmulhru_h(uint16_t rs1, uint16_t rs2);`  | RV32/64      |
| `__riscv_pmulhru_w`    | `uint32_t __riscv_pmulhru_w(uint32_t rs1, uint32_t rs2);`  | RV64 only    |
| `__riscv_pmulhsu_h`    | `int16_t __riscv_pmulhsu_h(int8_t rs1, uint8_t rs2);`      | RV32/64      |
| `__riscv_pmulhsu_w`    | `int32_t __riscv_pmulhsu_w(int16_t rs1, uint16_t rs2);`    | RV64 only    |
| `__riscv_pmulhsu_h_b0` | `int16_t __riscv_pmulhsu_h_b0(int8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pmulhsu_w_h0` | `int32_t __riscv_pmulhsu_w_h0(int16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_pmulhsu_h_b1` | `int16_t __riscv_pmulhsu_h_b1(int8_t rs1, uint8_t rs2);`   | RV32/64      |
| `__riscv_pmulhsu_w_h1` | `int32_t __riscv_pmulhsu_w_h1(int16_t rs1, uint16_t rs2);` | RV64 only    |
| `__riscv_pmulhrsu_h`   | `uint16_t __riscv_pmulhrsu_h(uint16_t rs1, int16_t rs2);`  | RV32/64      |
| `__riscv_pmulhrsu_w`   | `uint32_t __riscv_pmulhrsu_w(uint32_t rs1, int32_t rs2);`  | RV64 only    |
| `__riscv_mulh_h1`      | `int16_t __riscv_mulh_h1(int16_t rs1, int16_t rs2);`       | RV32 only    |
| `__riscv_mulhr`        | `int32_t __riscv_mulhr(int32_t rs1, int32_t rs2);`         | RV32 only    |
| `__riscv_mulhru`       | `uint32_t __riscv_mulhru(uint32_t rs1, uint32_t rs2);`     | RV32 only    |
| `__riscv_mulh_h0`      | `int16_t __riscv_mulh_h0(int16_t rs1, int16_t rs2);`       | RV32 only    |
| `__riscv_mulhsu_h0`    | `int16_t __riscv_mulhsu_h0(int16_t rs1, uint16_t rs2);`    | RV32 only    |
| `__riscv_mulhsu_h1`    | `int16_t __riscv_mulhsu_h1(int16_t rs1, uint16_t rs2);`    | RV32 only    |
| `__riscv_mulhrsu`      | `uint32_t __riscv_mulhrsu(uint32_t rs1, int32_t rs2);`     | RV32 only    |

## Register-pair Packed-SIMD Intrinsics(RV32 Only)

**Notes that all register-pair should use even number register.**

### Packed Immediate Load Intrinsics

| Intrinsic         | Signature                                       | Register Pairing              | Description                                                             |
| ----------------- | ----------------------------------------------- | ----------------------------- | ----------------------------------------------------------------------- |
| `__riscv_pli_db`  | `int64_t __riscv_pli_db(int imm);`  | `rd` is a **paired register** | Load an 8-bit immediate into both bytes of a destination register pair. |
| `__riscv_pli_dh`  | `int64_t __riscv_pli_dh(int imm);`  | `rd` is a **paired register** | Load a 16-bit signed immediate into each half of a destination pair.    |
| `__riscv_plui_dh` | `int64_t __riscv_plui_dh(int imm);` | `rd` is a **paired register** | Load a 16-bit upper immediate into each half of a destination pair.     |

### Packed Word-Pair Shift and Shift-Add Intrinsics

| Intrinsic          | Signature                                                 | Register Pairing              | Description                                                             |
| ------------------ | --------------------------------------------------------- | ----------------------------- | ----------------------------------------------------------------------- |
| `__riscv_pwslli_b` | `int64_t __riscv_pwslli_b(int rs1, int imm);`  | `rd` is a **paired register** | Shift each byte in a register pair left by an immediate value.          |
| `__riscv_pwslli_h` | `int64_t __riscv_pwslli_h(int rs1, int imm);`  | `rd` is a **paired register** | Shift each halfword in a register pair left by an immediate value.      |
| `__riscv_wslli`    | `int64_t __riscv_wslli(int rs1, int imm);`     | `rd` is a **paired register** | Shift full words in a register pair left by an immediate value.         |
| `__riscv_pwslai_b` | `int64_t __riscv_pwslai_b(int rs1, int imm);`  | `rd` is a **paired register** | Shift and add immediate for each byte in a register pair.               |
| `__riscv_pwslai_h` | `int64_t __riscv_pwslai_h(int rs1, int imm);`  | `rd` is a **paired register** | Shift and add immediate for each halfword in a register pair.           |
| `__riscv_wslai`    | `int64_t __riscv_wslai(int rs1, int imm);`     | `rd` is a **paired register** | Shift and add immediate for full words in a register pair.              |
| `__riscv_pwsll_bs` | `int64_t __riscv_pwsll_bs(int rs1, int rs2);` | `rd` is a **paired register** | Shift each byte in a register pair by values from another register.     |
| `__riscv_pwsll_hs` | `int64_t __riscv_pwsll_hs(int rs1, int rs2);` | `rd` is a **paired register** | Shift each halfword in a register pair by values from another register. |
| `__riscv_wsll`     | `int64_t __riscv_wsll(int rs1, int rs2);`     | `rd` is a **paired register** | Shift each word in a register pair by values from another register.     |
| `__riscv_pwsla_bs` | `int64_t __riscv_pwsla_bs(int rs1, int rs2);` | `rd` is a **paired register** | Shift and add for each byte using two source registers.                 |
| `__riscv_pwsla_hs` | `int64_t __riscv_pwsla_hs(int rs1, int rs2);` | `rd` is a **paired register** | Shift and add for each halfword using two source registers.             |
| `__riscv_wsla`     | `int64_t __riscv_wsla(int rs1, int rs2);`     | `rd` is a **paired register** | Shift and add for full words using two source registers.                |

### Packed Word-Pair Interleave Intrinsics

| Intrinsic         | Signature                                                | Register Pairing              | Description                                                                   |
| ----------------- | -------------------------------------------------------- | ----------------------------- | ----------------------------------------------------------------------------- |
| `__riscv_wzip8p`  | `int64_t __riscv_wzip8p(int rs1, int rs2);`  | `rd` is a **paired register** | Interleave 8-bit elements from two source registers into a destination pair.  |
| `__riscv_wzip16p` | `int64_t __riscv_wzip16p(int rs1, int rs2);` | `rd` is a **paired register** | Interleave 16-bit elements from two source registers into a destination pair. |

### Packed Word-Pair Arithmetic Intrinsics

| Intrinsic           | Signature                                                          | Register Pairing              | Description                           |
| ------------------- | ------------------------------------------------------------------ | ----------------------------- | ------------------------------------- |
| `__riscv_pwadd_b`   | `int64_t __riscv_pwadd_b(int32_t rs1, int32_t rs2);`   | `rd` is a **paired register** | Packed 8-bit signed addition.         |
| `__riscv_pwadd_h`   | `int64_t __riscv_pwadd_h(int32_t rs1, int32_t rs2);`   | `rd` is a **paired register** | Packed 16-bit signed addition.        |
| `__riscv_wadd`      | `int64_t __riscv_wadd(int32_t rs1, int32_t rs2);`      | `rd` is a **paired register** | Word-level signed addition.           |
| `__riscv_pwadda_b`  | `int64_t __riscv_pwadda_b(int32_t rs1, int32_t rs2);`  | `rd` is a **paired register** | Add and accumulate (signed 8-bit).    |
| `__riscv_pwadda_h`  | `int64_t __riscv_pwadda_h(int32_t rs1, int32_t rs2);`  | `rd` is a **paired register** | Add and accumulate (signed 16-bit).   |
| `__riscv_wadda`     | `int64_t __riscv_wadda(int32_t rs1, int32_t rs2);`     | `rd` is a **paired register** | Add and accumulate (word).            |
| `__riscv_pwaddu_b`  | `int64_t __riscv_pwaddu_b(int32_t rs1, int32_t rs2);`  | `rd` is a **paired register** | Packed 8-bit unsigned addition.       |
| `__riscv_pwaddu_h`  | `int64_t __riscv_pwaddu_h(int32_t rs1, int32_t rs2);`  | `rd` is a **paired register** | Packed 16-bit unsigned addition.      |
| `__riscv_waddu`     | `int64_t __riscv_waddu(int32_t rs1, int32_t rs2);`     | `rd` is a **paired register** | Word-level unsigned addition.         |
| `__riscv_pwaddau_b` | `int64_t __riscv_pwaddau_b(int32_t rs1, int32_t rs2);` | `rd` is a **paired register** | Add and accumulate (unsigned 8-bit).  |
| `__riscv_pwaddau_h` | `int64_t __riscv_pwaddau_h(int32_t rs1, int32_t rs2);` | `rd` is a **paired register** | Add and accumulate (unsigned 16-bit). |
| `__riscv_waddau`    | `int64_t __riscv_waddau(int32_t rs1, int32_t rs2);`    | `rd` is a **paired register** | Add and accumulate (word, unsigned).  |

### Packed Word-Pair Predicated Summation Intrinsics

| Intrinsic              | Signature                                                 | Register Pairing               | Description                                                                  |
| ---------------------- | --------------------------------------------------------- | ------------------------------ | ---------------------------------------------------------------------------- |
| `__riscv_predsum_dbs`  | `int32_t __riscv_predsum_dbs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Add signed byte elements in a register pair (`rs1`) to `rs2` and return sum. |
| `__riscv_predsum_dhs`  | `int32_t __riscv_predsum_dhs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Add signed halfword elements in `rs1` pair to `rs2` and return sum.          |
| `__riscv_predsumu_dbs` | `int32_t __riscv_predsumu_dbs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Add unsigned byte elements in `rs1` pair to `rs2` and return sum.            |
| `__riscv_predsumu_dhs` | `int32_t __riscv_predsumu_dhs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Add unsigned halfword elements in `rs1` pair to `rs2` and return sum.        |

### Packed Narrow shift right logical Intrinsics

| Intrinsic          | Signature                                         | Register Pairing               | Description                                                                |
| ------------------ | ------------------------------------------------- | ------------------------------ | -------------------------------------------------------------------------- |
| `__riscv_pnsrli_b` | `int32_t __riscv_pnsrli_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right logical on bytes in `rs1` pair, immediate shift amount. |
| `__riscv_pnsrli_h` | `int32_t __riscv_pnsrli_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right logical on halfwords in `rs1` pair, immediate shift.    |
| `__riscv_nsrli`    | `int32_t __riscv_nsrli(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Narrow shift right logical on words in `rs1` pair, immediate shift.        |

### Packed Narrow Clip Unsigned Intrinsics

| Intrinsic            | Signature                                           | Register Pairing               | Description                                                         |
| -------------------- | --------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------- |
| `__riscv_pnclipiu_b` | `int32_t __riscv_pnclipiu_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow clip unsigned byte elements from `rs1` with shift `imm`.     |
| `__riscv_pnclipiu_h` | `int32_t __riscv_pnclipiu_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow clip unsigned halfword elements from `rs1` with shift `imm`. |
| `__riscv_nclipiu`    | `int32_t __riscv_nclipiu(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Narrow clip unsigned word elements from `rs1` with shift `imm`.     |
| `__riscv_pnclipriu_b` | `int32_t __riscv_pnclipriu_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow clip right unsigned byte elements from `rs1` with shift `imm`.     |
| `__riscv_pnclipriu_h` | `int32_t __riscv_pnclipriu_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow clip right unsigned halfword elements from `rs1` with shift `imm`. |
| `__riscv_nclipriu`    | `int32_t __riscv_nclipriu(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Narrow clip right unsigned word elements from `rs1` with shift `imm`.     |

### Packed Narrow Shift Right Arithmetic Intrinsics

| Intrinsic          | Signature                                         | Register Pairing               | Description                                         |
| ------------------ | ------------------------------------------------- | ------------------------------ | --------------------------------------------------- |
| `__riscv_pnsrai_b` | `int32_t __riscv_pnsrai_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right arithmetic on byte elements.     |
| `__riscv_pnsrai_h` | `int32_t __riscv_pnsrai_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right arithmetic on halfword elements. |
| `__riscv_nsrai`    | `int32_t __riscv_nsrai(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Narrow shift right arithmetic on word elements.     |
| `__riscv_pnsrari_b` | `int32_t __riscv_pnsrari_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right arithmetic on byte elements with rounding.     |
| `__riscv_pnsrari_h` | `int32_t __riscv_pnsrari_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Narrow shift right arithmetic on halfword elements with rounding. |
| `__riscv_nsrari`    | `int32_t __riscv_nsrari(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Narrow shift right arithmetic on word elements with rounding.     |

### Packed Narrow Clip Intrinsics

| Intrinsic            | Signature                                           | Register Pairing               | Description                                                        |
| -------------------- | --------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------ |
| `__riscv_pnclipi_b`  | `int32_t __riscv_pnclipi_b(int64_t rs1, int imm);`  | `rs1` is a **paired register** | Signed narrow clip on byte elements with immediate.                |
| `__riscv_pnclipi_h`  | `int32_t __riscv_pnclipi_h(int64_t rs1, int imm);`  | `rs1` is a **paired register** | Signed narrow clip on halfword elements with immediate.            |
| `__riscv_nclipi`     | `int32_t __riscv_nclipi(int64_t rs1, int imm);`     | `rs1` is a **paired register** | Signed narrow clip on word elements with immediate.                |
| `__riscv_pnclipri_b` | `int32_t __riscv_pnclipri_b(int64_t rs1, int imm);` | `rs1` is a **paired register** | Signed narrow clip with rounding on byte elements (immediate).     |
| `__riscv_pnclipri_h` | `int32_t __riscv_pnclipri_h(int64_t rs1, int imm);` | `rs1` is a **paired register** | Signed narrow clip with rounding on halfword elements (immediate). |
| `__riscv_nclipri`    | `int32_t __riscv_nclipri(int64_t rs1, int imm);`    | `rs1` is a **paired register** | Signed narrow clip with rounding on word elements (immediate).     |
| `__riscv_pnclipu_bs`  | `int32_t __riscv_pnclipu_bs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Unsigned narrow clip on byte elements using register operand.     |
| `__riscv_pnclipu_hs`  | `int32_t __riscv_pnclipu_hs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Unsigned narrow clip on halfword elements using register operand. |
| `__riscv_nclipu`      | `int32_t __riscv_nclipu(int64_t rs1, int32_t rs2);`      | `rs1` is a **paired register** | Unsigned narrow clip on word elements.                            |
| `__riscv_pnclipru_bs` | `int32_t __riscv_pnclipru_bs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Unsigned narrow clip with rounding on byte elements.              |
| `__riscv_pnclipru_hs` | `int32_t __riscv_pnclipru_hs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Unsigned narrow clip with rounding on halfword elements.          |
| `__riscv_nclipru`     | `int32_t __riscv_nclipru(int64_t rs1, int32_t rs2);`     | `rs1` is a **paired register** | Unsigned narrow clip with rounding on word elements.              |
| `__riscv_pnclip_bs`  | `int32_t __riscv_pnclip_bs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Signed narrow clip on byte elements from register.                |
| `__riscv_pnclip_hs`  | `int32_t __riscv_pnclip_hs(int64_t rs1, int32_t rs2);`  | `rs1` is a **paired register** | Signed narrow clip on halfword elements from register.            |
| `__riscv_nclip`      | `int32_t __riscv_nclip(int64_t rs1, int32_t rs2);`      | `rs1` is a **paired register** | Signed narrow clip on word elements from register.                |
| `__riscv_pnclipr_bs` | `int32_t __riscv_pnclipr_bs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Signed narrow clip with rounding on byte elements (register).     |
| `__riscv_pnclipr_hs` | `int32_t __riscv_pnclipr_hs(int64_t rs1, int32_t rs2);` | `rs1` is a **paired register** | Signed narrow clip with rounding on halfword elements (register). |
| `__riscv_nclipr`     | `int32_t __riscv_nclipr(int64_t rs1, int32_t rs2);`     | `rs1` is a **paired register** | Signed narrow clip with rounding on word elements.                |

### Packed Shift and Arithmetic Instructions(Register-Pair Variant)

| Intrinsic            | Signature                                               | Register Pairing                     | Description                                                            |
| -------------------- | ------------------------------------------------------- | ------------------------------------ | ---------------------------------------------------------------------- |
| `__riscv_pslli_db`   | `int64_t __riscv_pslli_db(int64_t rs1, int imm);`       | `rd`, `rs1` are **paired registers** | Logical shift left on 8-bit elements.                                  |
| `__riscv_pslli_dh`   | `int64_t __riscv_pslli_dh(int64_t rs1, int imm);`       | `rd`, `rs1` are **paired registers** | Logical shift left on 16-bit elements.                                 |
| `__riscv_pslli_dw`   | `int64_t __riscv_pslli_dw(int64_t rs1, int imm);`       | `rd`, `rs1` are **paired registers** | Logical shift left on 32-bit elements.                                 |
| `__riscv_psll_dbs`   | `int64_t __riscv_psll_dbs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift left on 8-bit elements using register.                   |
| `__riscv_psll_dhs`   | `int64_t __riscv_psll_dhs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift left on 16-bit elements using register.                  |
| `__riscv_psll_dws`   | `int64_t __riscv_psll_dws(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift left on 32-bit elements using register.                  |
| `__riscv_psslai_dh`  | `int64_t __riscv_psslai_dh(int64_t rs1, int imm);`      | `rd`, `rs1` are **paired registers** | Shift left arithmetic immediate on 16-bit elements.                    |
| `__riscv_psslai_dw`  | `int64_t __riscv_psslai_dw(int64_t rs1, int imm);`      | `rd`, `rs1` are **paired registers** | Shift left arithmetic immediate on 32-bit elements.                    |
| `__riscv_pssha_dhs`  | `int64_t __riscv_pssha_dhs(int64_t rs1, int32_t rs2);`  | `rd`, `rs1` are **paired registers** | Shift left arithmetic with saturation on 16-bit elements.              |
| `__riscv_pssha_dws`  | `int64_t __riscv_pssha_dws(int64_t rs1, int32_t rs2);`  | `rd`, `rs1` are **paired registers** | Shift left arithmetic with saturation on 32-bit elements.              |
| `__riscv_psshar_dhs` | `int64_t __riscv_psshar_dhs(int64_t rs1, int32_t rs2);` | `rd`, `rs1` are **paired registers** | Shift left arithmetic with rounding and saturation on 16-bit elements. |
| `__riscv_psshar_dws` | `int64_t __riscv_psshar_dws(int64_t rs1, int32_t rs2);` | `rd`, `rs1` are **paired registers** | Shift left arithmetic with rounding and saturation on 32-bit elements. |
| `__riscv_psrl_dbs`   | `int64_t __riscv_psrl_dbs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift right on 8-bit elements.                                 |
| `__riscv_psrl_dhs`   | `int64_t __riscv_psrl_dhs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift right on 16-bit elements.                                |
| `__riscv_psrl_dws`   | `int64_t __riscv_psrl_dws(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Logical shift right on 32-bit elements.                                |
| `__riscv_psra_dbs`   | `int64_t __riscv_psra_dbs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Arithmetic shift right on 8-bit elements.                              |
| `__riscv_psra_dhs`   | `int64_t __riscv_psra_dhs(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Arithmetic shift right on 16-bit elements.                             |
| `__riscv_psra_dws`   | `int64_t __riscv_psra_dws(int64_t rs1, int32_t rs2);`   | `rd`, `rs1` are **paired registers** | Arithmetic shift right on 32-bit elements.                             |

### Packed Sign-Extension Instructions (Register-Pair Variant)

| Intrinsic            | Signature                                  | Register Pairing                     | Description                                                       |
| -------------------- | ------------------------------------------ | ------------------------------------ | ----------------------------------------------------------------- |
| `__riscv_psext_dh_b` | `int64_t __riscv_psext_dh_b(int64_t rs1);` | `rd`, `rs1` are **paired registers** | Sign-extend 8-bit elements in each half of a register pair.       |
| `__riscv_psext_dw_b` | `int64_t __riscv_psext_dw_b(int64_t rs1);` | `rd`, `rs1` are **paired registers** | Sign-extend 8-bit elements into 32-bit words in a register pair.  |
| `__riscv_psext_dw_h` | `int64_t __riscv_psext_dw_h(int64_t rs1);` | `rd`, `rs1` are **paired registers** | Sign-extend 16-bit elements into 32-bit words in a register pair. |

### Packed Absolute and Addition Instructions (Register-Pair Variant)

| Intrinsic          | Signature                                             | Register Pairing                     | Description                                                  |
| ------------------ | ---------------------------------------------- | ------------------------------------ | ------------------------------------------------------------ |
| `__riscv_psabs_db` | `int64_t __riscv_psabs_db(int64_t rs1);`              | `rd`, `rs1` are **paired registers** | Compute absolute value of signed 8-bit elements.             |
| `__riscv_psabs_dh` | `int64_t __riscv_psabs_dh(int64_t rs1);`              | `rd`, `rs1` are **paired registers** | Compute absolute value of signed 16-bit elements.            |
| `__riscv_padd_dbs` | `int64_t __riscv_padd_dbs(int64_t rs1, int32_t rs2);` | `rd`, `rs1` are **paired registers** | Add signed 8-bit elements pairwise between `rs1` and `rs2`.  |
| `__riscv_padd_dhs` | `int64_t __riscv_padd_dhs(int64_t rs1, int32_t rs2);` | `rd`, `rs1` are **paired registers** | Add signed 16-bit elements pairwise between `rs1` and `rs2`. |
| `__riscv_padd_dws` | `int64_t __riscv_padd_dws(int64_t rs1, int32_t rs2);` | `rd`, `rs1` are **paired registers** | Add 32-bit words between `rs1` and `rs2`.                    |

### Packed Register-Pair Packed Arithmetic Instructions

| Intrinsic           | Signature                                              | Register Pairing                            | Description                        |
| ------------------- | ------------------------------------------------------ | ------------------------------------------- | ---------------------------------- |
| `__riscv_padd_db`   | `int64_t __riscv_padd_db(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 8-bit signed addition       |
| `__riscv_padd_dh`   | `int64_t __riscv_padd_dh(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 16-bit signed addition      |
| `__riscv_padd_dw`   | `int64_t __riscv_padd_dw(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 32-bit signed addition      |
| `__riscv_addd`      | `int64_t __riscv_addd(int64_t rs1, int64_t rs2);`      | `rd`, `rs1`, `rs2` are **paired registers** | Doubleword vector addition         |
| `__riscv_psadd_db`  | `int64_t __riscv_psadd_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 8-bit signed addition    |
| `__riscv_psadd_dh`  | `int64_t __riscv_psadd_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 16-bit signed addition   |
| `__riscv_psadd_dw`  | `int64_t __riscv_psadd_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 32-bit signed addition   |
| `__riscv_paadd_db`  | `int64_t __riscv_paadd_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 8-bit signed addition    |
| `__riscv_paadd_dh`  | `int64_t __riscv_paadd_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 16-bit signed addition   |
| `__riscv_paadd_dw`  | `int64_t __riscv_paadd_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 32-bit signed addition   |
| `__riscv_psaddu_db` | `int64_t __riscv_psaddu_db(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 8-bit unsigned addition  |
| `__riscv_psaddu_dh` | `int64_t __riscv_psaddu_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 16-bit unsigned addition |
| `__riscv_psaddu_dw` | `int64_t __riscv_psaddu_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Saturated 32-bit unsigned addition |
| `__riscv_paaddu_db` | `int64_t __riscv_paaddu_db(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 8-bit unsigned addition  |
| `__riscv_paaddu_dh` | `int64_t __riscv_paaddu_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 16-bit unsigned addition |
| `__riscv_paaddu_dw` | `int64_t __riscv_paaddu_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired registers** | Averaging 32-bit unsigned addition |
| `__riscv_psub_db`   | `int64_t __riscv_psub_db(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 8-bit signed subtraction    |
| `__riscv_psub_dh`   | `int64_t __riscv_psub_dh(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 16-bit signed subtraction   |
| `__riscv_psub_dw`   | `int64_t __riscv_psub_dw(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired registers** | Packed 32-bit signed subtraction   |
| `__riscv_subd`      | `int64_t __riscv_subd(int64_t rs1, int64_t rs2);`      | `rd`, `rs1`, `rs2` are **paired registers** | Doubleword vector subtraction      |

### Packed Register-Pair Packed Pack/Unpack Instructions

| Intrinsic            | Signature                                               | Register Pairing                  | Description                                         |
| -------------------- | ------------------------------------------------------- | --------------------------------- | --------------------------------------------------- |
| `__riscv_ppack_dh`   | `int64_t __riscv_ppack_dh(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired** | Pack two signed 16-bit vectors into one 8-bit pair  |
| `__riscv_ppack_dw`   | `int64_t __riscv_ppack_dw(int64_t rs1, int64_t rs2);`   | `rd`, `rs1`, `rs2` are **paired** | Pack two signed 32-bit vectors into one 16-bit pair |
| `__riscv_ppackbt_dh` | `int64_t __riscv_ppackbt_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Pack bottom-top 16-bit vectors into 8-bit pair      |
| `__riscv_ppackbt_dw` | `int64_t __riscv_ppackbt_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Pack bottom-top 32-bit vectors into 16-bit pair     |
| `__riscv_ppacktb_dh` | `int64_t __riscv_ppacktb_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Pack top-bottom 16-bit vectors into 8-bit pair      |
| `__riscv_ppacktb_dw` | `int64_t __riscv_ppacktb_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Pack top-bottom 32-bit vectors into 16-bit pair     |
| `__riscv_ppackt_dh`  | `int64_t __riscv_ppackt_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Pack top half of 16-bit vectors                     |
| `__riscv_ppackt_dw`  | `int64_t __riscv_ppackt_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Pack top half of 32-bit vectors                     |

### Packed Register-Pair Saturating & Accumulating Add/Sub Instructions

| Intrinsic          | Signature                                             | Register Pairing                  | Description                                              |
| ------------------ | ----------------------------------------------------- | --------------------------------- | -------------------------------------------------------- |
| `__riscv_pas_dhx`  | `int64_t __riscv_pas_dhx(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **Add then Subtract** of double half-word vectors |
| `__riscv_psa_dhx`  | `int64_t __riscv_psa_dhx(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **Subtract then Add** of double half-word vectors |
| `__riscv_psas_dhx` | `int64_t __riscv_psas_dhx(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **Saturating Add then Subtract**                  |
| `__riscv_pssa_dhx` | `int64_t __riscv_pssa_dhx(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **Saturating Subtract then Add**                  |
| `__riscv_paas_dhx` | `int64_t __riscv_paas_dhx(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **Averaging Add then Subtract**                   |
| `__riscv_pasa_dhx` | `int64_t __riscv_pasa_dhx(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **Averaging Subtract then Add**                   |

### Packed Register-Pair Comparison Instructions 

| Intrinsic           | Signature                                              | Register Pairing                  | Description                                       |
| ------------------- | ------------------------------------------------------ | --------------------------------- | ------------------------------------------------- |
| `__riscv_pmseq_db`  | `int64_t __riscv_pmseq_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **equal** compare for 8-bit elements       |
| `__riscv_pmseq_dh`  | `int64_t __riscv_pmseq_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **equal** compare for 16-bit elements      |
| `__riscv_pmseq_dw`  | `int64_t __riscv_pmseq_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **equal** compare for 32-bit elements      |
| `__riscv_pmslt_db`  | `int64_t __riscv_pmslt_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed less-than** for 8-bit elements    |
| `__riscv_pmslt_dh`  | `int64_t __riscv_pmslt_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed less-than** for 16-bit elements   |
| `__riscv_pmslt_dw`  | `int64_t __riscv_pmslt_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed less-than** for 32-bit elements   |
| `__riscv_pmsltu_db` | `int64_t __riscv_pmsltu_db(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned less-than** for 8-bit elements  |
| `__riscv_pmsltu_dh` | `int64_t __riscv_pmsltu_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned less-than** for 16-bit elements |
| `__riscv_pmsltu_dw` | `int64_t __riscv_pmsltu_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned less-than** for 32-bit elements |

### Packed Register-Pair Min/Max Instructions

| Intrinsic          | Signature                                             | Register Pairing                  | Description                                    |
| ------------------ | ----------------------------------------------------- | --------------------------------- | ---------------------------------------------- |
| `__riscv_pmin_db`  | `int64_t __riscv_pmin_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed minimum** of 8-bit elements    |
| `__riscv_pmin_dh`  | `int64_t __riscv_pmin_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed minimum** of 16-bit elements   |
| `__riscv_pmin_dw`  | `int64_t __riscv_pmin_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed minimum** of 32-bit elements   |
| `__riscv_pminu_db` | `int64_t __riscv_pminu_db(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned minimum** of 8-bit elements  |
| `__riscv_pminu_dh` | `int64_t __riscv_pminu_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned minimum** of 16-bit elements |
| `__riscv_pminu_dw` | `int64_t __riscv_pminu_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned minimum** of 32-bit elements |
| `__riscv_pmax_db`  | `int64_t __riscv_pmax_db(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed maximum** of 8-bit elements    |
| `__riscv_pmax_dh`  | `int64_t __riscv_pmax_dh(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed maximum** of 16-bit elements   |
| `__riscv_pmax_dw`  | `int64_t __riscv_pmax_dw(int64_t rs1, int64_t rs2);`  | `rd`, `rs1`, `rs2` are **paired** | Packed **signed maximum** of 32-bit elements   |
| `__riscv_pmaxu_db` | `int64_t __riscv_pmaxu_db(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned maximum** of 8-bit elements  |
| `__riscv_pmaxu_dh` | `int64_t __riscv_pmaxu_dh(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned maximum** of 16-bit elements |
| `__riscv_pmaxu_dw` | `int64_t __riscv_pmaxu_dw(int64_t rs1, int64_t rs2);` | `rd`, `rs1`, `rs2` are **paired** | Packed **unsigned maximum** of 32-bit elements |
