This file outlines the detailed description of the daywise progress made in the internship so far:

Resources used for study can be found in the directory ```Reference-Material```

<h2>Week 1</h2>

<strong>Day 1 - </strong>```19/05/25```
  - Internship registration and other formalities
  - Revision of basics of embedded systems and IoT
  - Familiarization with some common terms:
    - Embedded Systems
    - SoC(System On Chip)
  - Revision of Computer Organization & Architecture
  - Familiarization with Zybo Z7-20 board:
    - its components and peripherals
    - study of different peripherals and their purpose
  - Start of study of zynq architecture[To be continued]

<strong>Day 2 - </strong>```20/05/25```
  - Study about Pmod AD1 Expansion Module
  - Familiarization with some more common terms:
    - IP(Intellectual Property)
    - LUT-6(6 input 1 output lookup table)
    - PCIe(Peripheral Component Interconnect Express)
    - MMCM(Mixed-Mode Clock Manager)
    - ACP(Accelerator Coherency Port)
    - NEON(ARM codename for Vector Processing Unit(VPU))
    - GigE(Gigabit Ethernet)
  - Study of Zynq architecture and 7 series FPGA architecture:[continuation]
    - 7 series FPGA architecture: Common elements, Logic resources, 7 series Block RAM and FIFO, XADC, AMS(Analog Mixed Signal)
    - Overview of PS(Processing System) & PL(Programmable Logic) in Zynq architecture
    - Study of Zynq SoC Block diagram
    - Main components of PS and PL
    - PS-PL interface[To be continued]
    
<strong>Day 3 - </strong>```21/05/25```
  - Study of Zynq architecture:[continuation]
    - PS peripherals and connections(mainly MIO, EMIO and GPIO)
  - Study of some common communication protocols:
    - SPI(Serial Peripheral Interface)
    - I2C(Inter-Integrated Circuit)
    - CAN(Controller Area Network)
    - UART(Universal Asynchronous Receiver Transmitter)
  - Comparison between the aforementioned protocols in terms of speed and hardware complexity
  - Trying to display Hello World using UART on Zynq Processor on Xilinx Zedboard using Xilinx Vivado and Xilinx Vitis[To be continued]
    - Created Block Design and then generated bitstream in Vivado
    - Exported Hardware design in Vivado
    - Made Platform & Application project from exported ```.xsa``` file in Vitis
    - Wrote simple "Hello World" in Vitis, build project and lauch on hardware
    - ERROR: Nothing was showing up on the serial terminal, even after doing the aforementioned steps[To be continued]
      - Tried with software like putty and minicom to observe serial terminal but same error crept in
      - checked the USB port to see if it was working properly(using a loopback connector<sup>*</sup> in a USB to RS-232 cable) but it was not the issue
      - checked the two connections(one to PROG and other to UART) to the board and the power connection, but no issue there

<strong>Day 4 - </strong>```22/05/25``` 
  - Trying to display Hello World using UART on Zynq Processor on Xilinx Zedboard using Xilinx Vivado and Xilinx Vitis[continuation]
    - Issue resolved: The UART0 was getting mapped to EMIO peripheral and causing error
    - Successfully displayed "Hello World" on both vitis emulator and putty(serial connection to ttyACM0 port)
  - Study of basics of Operating Systems(OS)[To be continued]

<strong>Day 5 - </strong>```23/05/25``` 
  - Study of basics of Operating Systems(OS)[continuation]
  - Study of bitstream and netlist
  - Familiarization with Xilinx Zedboard:
    - its components and peripherals
    - study of different peripherals and their purpose using Zedboard datasheet
  - Implementation of GPIO via MIO on Zedboard
    - Created block design(removing some peripherals from Block Design to decrease build time of final vitis application project) in Vivado
    - Generated bitstream and then exported hardware design in Vivado
    - Made Platform and Application project from exported ```.xsa``` file in Vitis
    - Wrote a bare metal C program to
      - read input from PS GPIO pin 50(push button)
      - write input data to PS GPIO pin 7(built-in LED)
      - control the Pmod pins according to the input data(the input read from PS GPIO pin 50)
    - Analyzed the waveform at the Pmod pin on a Multimeter, and then on a Digital Oscilloscope
    - The waveform was square, in accordance with the code
    - The time period and duty cycle of the square waveform were as calculated


<sup>*</sup> The loopback connector was connected to the RS-232 cable and the USB cable was connected to the port to check. Then, the terminal was opened and the command ```ls \dev\tty*``` was executed, this showed the ports in the system. The name of the port was then identified(by connecting and disconnecting USB cable or knowing beforehand), which was ttyUSB0 in my case. Then this port was emulated using PuTTY or minicom, to let us interact with the port. When we type a character, let's say ```a```, then that character is repeated in the terminal(because of the loopback connector), like ```aa```. If the typed character is repeated, then the USB port is working correctly. Basically, the loopback connector shorts the transmitter and receiver.


