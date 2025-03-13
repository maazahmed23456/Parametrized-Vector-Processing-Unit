# Parametrized-Vector-Processing-Unit
A parametrized functional unit that can be reconfigured into multiple parallel mixed precision ALU's for vector computations.

## A Glance at the FP Multiplier Architecture

- Project Title: Parametrized Vector Processing Unit for SIMD parallel computations.
- Author: Shaik Maaz Ahmed
- Date: 13/03/2025
- Institution/Organization: National Institute of Technology Andhra Pradesh
- Version: 1.0


## Block Diagram of the ALU

 <p align="center">
  <img width="500" height="500" src="/Images/Screenshot 2025-03-13 122353.png">
</p>

## 1. Overview
- Objective: Design and implement a functional unit that can processes vectors parallelly
- Technology Node: 90nm
- Design Flow: RTL to GDSII using Cadence EDA Tools and AMD Xilinx Vivado
- Target Application: Matrix Computations , ML applications , GPU applications


## 2. Project Scope
- Design Goals: Power, Performance, Area (PPA) trade-offs
- Architecture: SIMD , Parallel Processing 
- Supported Operations: 32-bit floating point , 32-bit fixed point

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
Timing Summary: Met setup/hold constraints?
Power Analysis: Dynamic, Static power
Area Report: Gate count, cell utilization
Performance Metrics: Throughput, Latency


## RTL Design and Functional Verification

### Schematic view of VPU

 <p align="center">
  <img width="500" height="500" src="/Images/VPU.png">
</p>


### Schematic view of ALU

<p align="center">
  <img width="500" height="500" src="/Images/ALU.png">
</p>


### Simulation Results
- **ALU**
 <p align="center">
  <img width="500" height="500" src="/Images/FP MULT (NEW).png">
</p>

<p align="center">
  <img width="500" height="500" src="/Images/INT MULT , ADD ,AND OR XOR (NEW) ALU.png">
</p>

**VPU**
<p align="center">
  <img width="500" height="500" src="/Images/VPU FP MULT (NEW).png">
</p>

<p align="center">
  <img width="500" height="500" src="/Images/VPU INT MULT (NEW).png">
</p>

<p align="center">
  <img width="500" height="500" src="/Images/DOT PRODUCT.png">
</p>


## Synthesis

### Netlist View

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Area Report

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Power Report

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Timing Report

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Gates Report

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

It shows the FP Multiplier was synthesiszed by ustilisation of only 59 LUT and 2 DSP and 99 I/O ports which is fair utilization.

## Physical Design
The design was imported to Openlane on linux and a configuration script was developed which performed the synthesis to gds steps. Openlane is an open-source EDA tools that is used to perfrom the ASIC flow. The design was implemented by leveraging Skywater 130nm pdk.

### Design Summary

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Placed Design

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>


### Routed Design

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>

### Post-Route Timing Report

 <p align="center">
  <img width="800" height="500" src="/SCHEMATIC AND WAVEFORMS/SCHEMATIC.png">
</p>


***************



## Future Work

- Design the division , adder and subtractor modules in similar floating point operation
- Integrate all the modules into a Floating Point ALU with opcode and clock for operation at highest frequency possible
- Perform the RTL to GDS flow of the FP ALU in Cadence or Synopsys EDA Tools or Openlane ASIC Flow
- Fabricate the chip for real time testing

## Contributors 

- **Maaz Ahmed**  

## Acknowledgments

- Dr.Ediga Raghuveera , AdHoc Faculty , NIT AP (mentor)
- Dr.Kiran Kumar Gurrala , Assistant Professor , NIT AP
- Dr.Puli Kishore Kumar , Assistant Professor , NIT AP
- Harika Banala , PhD , NIT AP

## Contact Information

- Shaik Maaz Ahmed , maazahmed23456@gmail.com
