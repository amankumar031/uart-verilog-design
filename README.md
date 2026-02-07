**UART DESIGN AND VERIFICATION USING VERILOG HDL**

**Abstract**

This project presents the design and simulation of a Universal Asynchronous Receiver Transmitter (UART) implemented using Verilog Hardware Description Language (HDL). The system supports serial data transmission and reception using a standard UART frame format, including start bit, data bits, and stop bit. A baud rate generator with 16× oversampling is employed to ensure reliable data sampling. Functional correctness is verified through simulation and waveform analysis.

**1. Introduction**

UART is one of the most widely used serial communication protocols in digital systems due to its simplicity and minimal hardware requirements. It enables asynchronous communication between devices without the need for a shared clock. This project demonstrates a complete UART system implemented in Verilog, focusing on modular design, finite state machine (FSM) control, and simulation-based verification.

**2. System Architecture**

The UART system consists of the following main components:

Baud Rate Generator

UART Transmitter (TX)

UART Receiver (RX)

Top-Level Integration Module

Testbench for Functional Verification

The transmitter and receiver are internally connected in a loopback configuration to validate end-to-end data transfer.

**3. Module Description**

**3.1 Baud Rate Generator**

The baud rate generator produces a periodic timing pulse used as a reference for both the transmitter and receiver. The generator is parameterized using a threshold value and generates a 16× oversampling tick, which improves receiver accuracy.

**3.2 UART Transmitter (TX)**

The transmitter converts 8-bit parallel data into a serial data stream. Transmission is controlled using a finite state machine with the following states:

IDLE – Line remains in logic HIGH state

START – Transmission of the start bit (logic LOW)

DATA – Serial transmission of 8 data bits (LSB first)

STOP – Transmission of stop bit (logic HIGH)

Each bit duration is controlled using the baud rate tick.

**3.3 UART Receiver (RX)**

The receiver reconstructs serial data into an 8-bit parallel format. It uses 16× oversampling to sample incoming data at the center of each bit period. Upon successful reception of a complete byte, a rx_done signal is asserted to indicate valid data availability.

**3.4 Top-Level Module**

The top-level module integrates the baud rate generator, UART transmitter, and UART receiver. The transmitter output is directly connected to the receiver input, enabling internal loopback testing without external hardware.

**3.5 Testbench**

The testbench performs the following operations:

Generates a stable clock signal

Applies system reset

Initiates data transmission using a start pulse

Sends an 8-bit test value (0x77)

Waits for reception completion

Displays received data and records waveform output

Waveform dumping is enabled using VCD files for detailed signal analysis.

**4. Simulation and Results**

Simulation results confirm correct UART operation, including:

Proper baud timing

Correct FSM transitions

Accurate serialization and deserialization

Successful reception of transmitted data

The transmitted byte 0x77 is correctly received at the output, validating the functional correctness of the design. Waveforms are analyzed using EPWave/GTKWave to observe internal signals and timing behavior.

**5. Tools and Technologies**

Verilog HDL

EPWave / GTKWave (Waveform Analysis)

GitHub (Version Control and Documentation)

**6. Conclusion**

This project successfully demonstrates the design and verification of a UART communication system using Verilog HDL. The modular architecture and FSM-based control provide a clear understanding of UART operation. The design serves as a strong foundation for further extensions such as FPGA implementation or configurable baud rate support.

**Author**
Aman Kumar
Microelectronics and VLSI Engineering
