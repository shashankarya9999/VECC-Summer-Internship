This file outlines the detailed description of the daywise progress made in the internship so far:

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
    - Made Platform & Application project from exported ```.xsa```file in Vitis
    - Wrote simple "Hello World" in Vitis, build project and lauch on hardware
    - ERROR: Nothing was showing up on the serial terminal, even after doing the aforementioned steps[To be continued]
      - Tried with software like putty and minicom to observe serial terminal but same error crept in
      - checked the USB port to see if it was working properly but it was not the issue
      - checked the two connections(one to PROG and other to UART) to the board and the power cable, but no issue there

<strong>Day 4 - </strong>```22/05/25``` 
  - Trying to display Hello World using UART on Zynq Processor on Xilinx Zedboard using Xilinx Vivado and Xilinx Vitis[continuation]
    - Issue resolved: The UART0 was getting mapped to EMIO peripheral and causing error
    - Successfully displayed "Hello World" on both vitis emulator and putty(serial connection to ttyACM0 port)
  - Study of basics of Operating Systems(OS)

