# UART-Transmitter-Receiver-Verilog
Designed a UART (Universal Asynchronous Receiver Transmitter) IP Core in Verilog HDL featuring FSM-based transmission and reception, baud rate generation, RTL simulation, and waveform verification.
# UART IP Core in Verilog HDL

## Overview

This project implements a synthesizable UART (Universal Asynchronous Receiver Transmitter) IP Core in Verilog HDL. The design follows a modular RTL architecture and includes UART transmission, baud rate generation, simulation, and verification.

The project was developed to gain hands-on experience in RTL Design, Finite State Machine (FSM) implementation, digital communication protocols, and hardware verification methodologies commonly used in FPGA and ASIC design flows.

---

## Features

- UART Transmitter (TX)
- UART Receiver (RX) *(Work in Progress)*
- Baud Rate Generator
- FSM-Based Control Logic
- Parameterized Design
- RTL Simulation and Verification
- Synthesizable Verilog HDL
- Waveform Analysis using EPWave

---

## System Architecture

```text
                +----------------+
                | Baud Generator |
                +--------+-------+
                         |
                         v

+-----------+      +------------+      Serial Data
|  Data In  | ---> |  UART TX   | ------------------>
+-----------+      +------------+

```

---

## UART Frame Format

```text
Idle | Start Bit | Data[7:0] | Stop Bit

 1         0      LSB First      1
```

Example Transmission of ASCII Character 'A' (0x41):

```text
Data = 01000001

Frame:

0 1 0 0 0 0 0 1 0 1
^                 ^
Start           Stop
```

---

## Finite State Machine (FSM)

The UART transmitter is implemented using a finite state machine consisting of the following states:

```text
IDLE
  |
  v
START
  |
  v
DATA
  |
  v
STOP
  |
  +------> IDLE
```

### State Description

| State | Description |
|---------|------------|
| IDLE | Waits for transmission request |
| START | Sends UART start bit |
| DATA | Transmits 8-bit data payload |
| STOP | Sends stop bit and returns to idle |

---

## Project Structure

```text
UART-IP-Core-Verilog/

├── rtl/
│   ├── uart_tx.v
│   ├── uart_rx.v
│   └── baud_gen.v
│
├── tb/
│   └── uart_tb.v
│
├── docs/
│   ├── architecture.png
│   └── waveform.png
│
├── README.md
│
└── LICENSE
```

---

## Simulation Environment

### Tools

- Verilog HDL
- EDA Playground
- Icarus Verilog
- EPWave
- GitHub

### Running Simulation

Compile:

```bash
iverilog -o uart_sim rtl/*.v tb/*.v
```

Run:

```bash
vvp uart_sim
```

View Waveform:

```bash
gtkwave wave.vcd
```

---

## Verification

A dedicated testbench was developed to verify UART transmission functionality.

### Test Cases

| Test Case | Status |
|------------|--------|
| Reset Functionality | PASS |
| Single Byte Transmission | PASS |
| Start Bit Generation | PASS |
| Data Bit Transmission | PASS |
| Stop Bit Generation | PASS |

---

## Sample Waveform

(Add waveform screenshot here)

---

## RTL Design Concepts Demonstrated

- Register Transfer Level (RTL) Design
- Verilog HDL Coding
- Finite State Machines (FSM)
- Sequential Logic Design
- Combinational Logic Design
- Digital Communication Protocols
- Simulation and Verification
- Waveform Debugging

---

## Future Enhancements

- UART Receiver (RX)
- FIFO Buffer Integration
- Configurable Data Width
- Configurable Stop Bits
- SystemVerilog Testbench
- Functional Coverage
- UVM-Based Verification Environment
- FPGA Implementation

---

## Learning Outcomes

Through this project, the following concepts were implemented and verified:

- UART Communication Protocol
- FSM-Based Controller Design
- RTL Coding Best Practices
- Simulation-Driven Verification
- Hardware Debugging using Waveforms

---

## Author

**Sanket Saste**

BS in Electronic Systems  
Interested in RTL Design, Verification, FPGA Design, and VLSI Engineering.

GitHub: *(Add your GitHub profile link here)*

---

## License

This project is released under the MIT License.
