# Parametrized-Vector-Processing-Unit
A parametrized functional unit that can be reconfigured into multiple parallel lanes of ALU's for vector computations. The ALU supports both 32-bit floating point and fixed point formats.

- Project Title: Parametrized Vector Processing Unit for SIMD parallel computations.
- Author: Shaik Maaz Ahmed
- Date: 13/03/2025
- Institution: National Institute of Technology Andhra Pradesh
- Version: 1.0


## Block Diagram of the ALU

 <p align="center">
  <img width="1000" height="500" src="/Images/Screenshot 2025-03-13 122353.png">
</p>

## 1. Overview
- Objective: Design and implement a functional unit that can processes vectors parallelly
- Technology Node: 90nm
- Design Flow: RTL to GDSII using Cadence EDA Tools and AMD Xilinx Vivado
- Target Application: Matrix Computations , ML applications , GPU applications
  
### Inputs and Outputs information
- **Vectorized Input Width:** `A[N*32-1:0]`, `B[N*32-1:0]` (Each element is **32-bit**)  
- **Vectorized Output Width:** `Result[N*64-1:0]` (**64-bit** per element)  
- **Carry Output:** `Cout[N-1:0]` (One carry-out per ALU instance)  
- **Dot Product Output:** `Dot_Product[63:0]` (Final accumulated **dot product** result)

  
### ALU Opcode Functions

| **Opcode (mode)** | **Operation**                     | **Output Register** |
|-------------------|----------------------------------|---------------------|
| `4'b0000` (`0x0`) | Floating-Point Multiply (FP Mult) | `{32'b0, mult_out}` |
| `4'b0001` (`0x1`) | Floating-Point Addition (FP Add) | `{32'b0, add_out}` |
| `4'b0010` (`0x2`) | Bitwise AND                      | `{32'b0, logic_out}` |
| `4'b0011` (`0x3`) | Bitwise OR                       | `{32'b0, logic_out}` |
| `4'b0100` (`0x4`) | Bitwise XOR                      | `{32'b0, logic_out}` |
| `4'b0101` (`0x5`) | Logical Left Shift (LSL)         | `{32'b0, logic_out}` |
| `4'b0110` (`0x6`) | Logical Right Shift (LSR)        | `{32'b0, logic_out}` |
| `4'b0111` (`0x7`) | Arithmetic Right Shift (ASR)     | `{32'b0, logic_out}` |
| `4'b1000` (`0x8`) | Integer Multiplication (Lower 32 bits) | `product` (64-bit result) |
| `4'b1001` (`0x9`) | Integer Addition (with carry-in) | `{32'b0, sum}` |


## 2. Architecture

### Modules  
- **ALU Core:**  
  - Configurable **N-parallel ALU instances**, each performing independent operations on vector elements.  
  - Supports both **integer and floating-point arithmetic**, with dedicated processing units for each.  

- **Dot Product Unit:**  
  - Computes the **dot product** across `N` elements using parallel ALU outputs.  

### Parallelism & Performance  
- **Instruction Execution:**  
  - **SIMD-style** execution, enabling parallel operations on multiple vector elements.  

- **Pipeline Stages:**  
  - **Single-cycle execution** for integer operations.  
  - **Multi-cycle execution** for floating-point operations.  

- **Optimized For:**  
  - **Matrix operations**, **vector computations**, and **image transformations**.  
  - **Pixel-wise processing**, similar to **scalar processors in modern GPU architectures**.  


## 3. Workflow
- **RTL Design**
- HDL: Verilog 
- Simulation: AMD Xilinx Vivado
- Verification Metrics: Mode based output results
- **Synthesis**
- Tool: Cadence Genus
- Library: 90nm standard cell library
- Timing Constraints: Provided in SDC format
- Reports: Area, Timing, Power
- **Place & Route**
- Tool: Cadence Innovus
- Floorplan: Aspect ratio - 0.7 , Core Utilization - 70%

## 4. Results

## RTL Design and Functional Verification

### Schematic view of VPU

 <p align="center">
  <img width="800" height="500" src="/Images/VPU.png">
</p>


### Schematic view of ALU

<p align="center">
  <img width="1000" height="500" src="/Images/ALU.png">
</p>


### Simulation Results
- **ALU Floating Point Multiplication**
 <p align="center">
  <img width="1000" height="500" src="/Images/FP MULT (NEW).PNG">
</p>

- **ALU Integer Multiplication, Addition and Logical AND, OR, XOR**
<p align="center">
  <img width="1000" height="500" src="/Images/INT MULT , ADD ,AND OR XOR (NEW) ALU.PNG">
</p>

- **VPU Floating Point Multiplication**
<p align="center">
  <img width="1000" height="500" src="/Images/VPU FP MULT (NEW).PNG">
</p>

- **VPU Integer Multiplication**
<p align="center">
  <img width="1000" height="500" src="/Images/VPU INT MULT (NEW).PNG">
</p>

- **VPU Dot Porduct**
<p align="center">
  <img width="1000" height="500" src="/Images/DOT PRODUCT.PNG">
</p>


## Synthesis

**Inputs** - Verilog(.v) , Timing Library (.lib) , TCL Script (.tcl) files

### Netlist View

<p align="center">
  <img width="1000" height="500" src="/Images/SYNTHESIZED NETLIST.png">
</p>

### Area Report
The synthesized design occupies an area of 0.114288 mm² of area

 <p align="center">
  <img width="1000" height="500" src="/Images/AREA.png">
</p>

### Power Report
The synthesized design consumes 6.22 mW of power

<p align="center">
  <img width="1000" height="500" src="/Images/POWER.png">
</p>

### Timing Report
- Clock Edge: 10,000 ps
- Data Path Delay: 4,470 ps
- Required Time: 9,906 ps
- Slack: 5,436 ps (No setup violation)

 <p align="center">
  <img width="1000" height="500" src="/Images/TIMING.png">
</p>

### Gates Report
The synthesized design uses 12782 standard cells

<p align="center">
  <img width="1000" height="500" src="/Images/GATES.png">
</p>


## Physical Design

**Inputs** - Netlist(.v) , Constraint File (.sdc) , Timing Libraries (.lib) , Technology Files (.lef) , MMMC configuration (.mmmc) files

### Design Summary

 <p align="center">
  <img width="1000" height="500" src="/Images/DESIGN SUMMARY (BERFORE IMPLEMENTATION).png">
</p>

### Floorplan
- Aspect Ratio - 1
- Core Utilization - 70%
- Core to I/0 - 15um from all sides
- 

### Placed Design

<p align="center">
  <img width="1000" height="500" src="/Images/PLACED.png">
</p>


### Routed Design

<p align="center">
  <img width="1000" height="500" src="/Images/ROUTED.png">
</p>

### Post-Route Timing Report

<p align="center">
  <img width="1000" height="500" src="/Images/POST ROUTE TIMING REPORT.png">
</p>


***************



## References

- [1] M. F. Tolba, A. H. Madian and A. G. Radwan, "FPGA realization of ALU for mobile GPU," 2016 3rd International Conference on Advances in Computational Tools for Engineering Applications (ACTEA), Zouk Mosbeh, Lebanon, 2016, pp. 16-20, doi: 10.1109/ACTEA.2016.7560104. keywords: {Table lookup;Delays;Adders;Field programmable gate arrays;Program processors;Logic gates;ALU;GPU;Multiplier;CLA;LUT Multiplier;Verilog;Xilinx;FPGA},

- [2] A. Y. N J and A. V R, "FPGA Implementation of a High Speed Efficient Single Precision Floating Point ALU," 2023 International Conference on Control, Communication and Computing (ICCC), Thiruvananthapuram, India, 2023, pp. 1-5, doi: 10.1109/ICCC57789.2023.10165441. keywords: {Power demand;Program processors;Simulation;Computer architecture;Dynamic range;Hardware;Hardware design languages;IEEE 754;ALU;FPGA;RISC V ISA;Exceptions},



## Contributors 

- **Maaz Ahmed**  

## Acknowledgments

- Dr.Kiran Kumar Gurrala , Assistant Professor , NIT AP
- Dr.Puli Kishore Kumar , Assistant Professor , NIT AP
- Chaitanya Krishna , PhD , NIT AP
- Harika Banala , PhD , NIT AP

## Contact Information

- Shaik Maaz Ahmed , maazahmed23456@gmail.com
