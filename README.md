# APB Slave Module Design

## Overview
This project implements an Advanced Peripheral Bus (APB) Slave Module based on the AMBA (Advanced Microcontroller Bus Architecture) protocol by ARM.  
The APB slave acts as an interface between peripheral devices and the system bus, enabling low-bandwidth communication with minimal power consumption and reduced complexity.

## Objective
The objective of this project is to design, implement, and verify an APB slave interface that:
- Communicates efficiently with an AHB/APB bridge or master.
- Performs read and write operations to internal registers.
- Ensures proper timing and protocol compliance as per the APB specification.

## Design Description
- Language Used: Verilog HDL  
- Simulation Tool: Xilinx Vivado / ModelSim  

### Design Inputs
- PCLK – APB clock  
- PRESETn – Active-low reset  
- PSEL – Slave select signal  
- PENABLE – Enable signal for data phase  
- PWRITE – Write control signal  
- PADDR – Address bus (for selecting register)  
- PWDATA – Write data bus  

### Design Outputs
- PRDATA – Read data bus  
- PREADY – Ready signal to indicate completion  
- PSLVERR – Error signal for protocol violations  

## Functional Operation
1. Setup Phase:  
   The master asserts PSEL and provides the address (PADDR), data (PWDATA), and control signals (PWRITE).  

2. Enable Phase:  
   The master asserts PENABLE. The slave responds with PREADY = 1 when the operation is completed.  

3. Read/Write Operations:  
   - Write Operation: Data from PWDATA is written into internal registers.  
   - Read Operation: Data is driven onto the PRDATA bus.  

## Verification
A Verilog testbench was developed to verify:
- Correct read and write transactions.  
- Proper timing behavior and protocol handshake.  
- Reset and error handling.  

Functional and timing simulations were successfully performed.

## Results
- APB protocol handshake verified through waveform analysis.  
- Successful read and write operations observed from slave registers.  
- All signal transitions followed standard APB timing.

## Block Diagram
<img width="700" height="352" alt="image" src="https://github.com/user-attachments/assets/aa71b59a-47f5-4638-9861-6c629d7f8baf" />




