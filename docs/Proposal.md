# Statement of purpose:

This chip will be a design for an 8-bit processor with a custom ISA. Instructions will be stored on RP2040. Chip will contain registers, ALU, and output register

# System Diagram:

<img width="975" height="384" alt="image" src="https://github.com/user-attachments/assets/1a30f948-fc32-4b93-8a09-51c6c4c62de8" />

PC sends address of the next instruction to RP 2040 which then sends that instruction. Control Logic decodes instruction and instructs the Datapath. Value of output register is then sent to RP2040.

# IO Pin assignment Table

| Pin           | Direction | Name        | Width | Function                           |
|---------------|-----------|-------------|-------|------------------------------------|
| clk           | In        | Clock       | 1     | System clock                       |
| rst_n         | In        | Reset       | 1     | Set PC to 0 and reset output       |
| ena           | In        | Enable      | 1     | N/C                                |
| ui_in\[7:0\]  | In        | instruction | 8     | RP 2040 instruction                |
| uo_out\[7:0\] | Out       | Output      | 8     | Value inside output register       |
| Uio\[5:0\]    | Out       | PC          | 6     | Program counter sent to RP 2040 to |
| Uio\[6:7\]    | Out       | X           | 2     | Undecided use                      |

# Proposed Specification

- This processor will aim to have 8 registers with the possibility to up to 20 instructions.

- An accumulator register will be used to reduce register space in the instructions.

- Will have R-type and I/J-type instructions

- MSB will be the op code

**R-Type**

| OP code \[7\] (0)| Function\[6:3\] | Reg\[2:0\] |
|------------------|-----------------|------------|

| Instruction | Function |
|-|-|
|ADD|0000|
|SUB|0001|
|XOR|1000|
|OR|1100|
|AND|1110|
|LOAD|0100|
|STORE|0110|
|SLL|1010|
|SRL|1011|


**I/J-Type**

| OP code \[7\] (1)| Function\[6:5\] | Immediate\[4:0\] |
|------------------|-----------------|------------------|

| Instruction | Function |
|-|-|
|ADDI|00|
|LOADI|01|


# Instructions



# Timeline for Completion

| Week                | Milestone                  |
|---------------------|----------------------------|
| Week 1 (Oct 8th)    | Architecture/ISA           |
| Week 2-5 (Nov 5th)  | Write code and simulations |
| Week 6-8 (Nov 22nd) | Testing and debugging      |
| Week 9 (Nov 29th)   | Final Submission           |

# Distribution of Work

| **Task**                                                    | **Owner**   |
|-------------------------------------------------------------|-------------|
| ISA, instruction encoding and pin assignment                | All members |
| ALU and register file (including accumulator)               | Ben         |
| Control logic, instruction decoder and PC                   | Mohammad    |
| Top-level integration and IO (output register, pin mapping) | Mohammad    |
| RP 2040 Firmware                                            | Ben         |
| Assembler                                                   | Mohammad    |
| Instruction-level and program-level simulation tests        | All members |
| Debugging and fixes                                         | All members |
| Documentation, final review and submission                  | All members |
