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

<h2>Week 2</h2>

<strong>Day 6 - </strong>```26/05/25```
  - Study of Embedded Control Systems[To be continued]
    - Why we need embedded system for accelerator control?
    - Types of embedded systems based on OS type - Bare Metal, Embedded OS & Linux Based
    - Examples of embedded systems - MCU(microcontroller) based, CPU/MPU(microprocessor) based
    - Difference between RISC-V and ARM
    - Typical Embedded System block diagram and example
    - Disadvantages of COTS(Commercial-Off-The-Shelf) products and need of SoM(System-On-Module)
    - Advantages of SoM design
    - Custom-made Embedded Control Board design involves 3 major steps - Hardware design, Linux OS design & EPICS design.
  - Remote work setup<sup>**</sup> for Xilinx Vivado and Xilinx Vitis        
  - Implementation of GPIO via EMIO on Zedboard[To be continued]
    - Created block design in Vivado 

<strong>Day 7 - </strong>```27/05/25```
  - Implementation of GPIO via EMIO on Zedboard[To be continued]
    - Added a ```.xdc``` constraint file in the Vivado project
    - Generated bitstream and then exported hardware design in Vivado
    - Made Platform and Application project from exported ```.xsa``` file in Vitis
    - Error in Vitis<sup>***</sup> solved
    - Wrote a bare metal C program to
      - read input from push buttons and switches
      - write input data to LEDs according to the input at the push buttons and switches
    - Wrote another bare metal C program to[To be continued]
      - take current bit pattern of the 8 LEDS(L0 to L7)
      - and if a button is pressed, then increase the count of the binary number represented by the LED bit pattern by 1
      - and update LED bit pattern accordingly
  

<sup>*</sup> The loopback connector was connected to the RS-232 cable and the USB cable was connected to the port to check. Then, the terminal was opened and the command ```ls \dev\tty*``` was executed, this showed the ports in the system. The name of the port was then identified(by connecting and disconnecting USB cable or knowing beforehand), which was ttyUSB0 in my case. Then this port was emulated using PuTTY or minicom, to let us interact with the port. When we type a character, let's say ```a```, then that character is repeated in the terminal(because of the loopback connector), like ```aa```. If the typed character is repeated, then the USB port is working correctly. Basically, the loopback connector shorts the transmitter and receiver.

<sup>**</sup> There is a remote server on which we wanted to run Vivado & Vitis software. So, we used a remote desktop client ```Remmina``` to remotely access the server. But our work required us to program the Zedboard which couldn't be done without a hardware server. The hardware server(```hw_server```) is required to connect our Zedboard on local computer to the remote server. To do so, a hardware server program(typing command ```hw_server``` in the terminal) is ran on the local computer and a client program of hardware manager is ran(in Vivado) on the remote server. The hw_server creates a TCP port 3121 for connection with the remote server's client program. This ensures that Zedboard can be connected and programmed on the remote server(When we open Hardware manager and open new target, the board is shown as connected).   

<sup>***</sup> The board was showing as connected in Vivado in remote server, but there was an error in Vitis. Some error like "Could not find ARM device on connection: Local" was coming when I was trying to launch the application project on the hardware(Zedboard). We created a new configurations for the launch and incorporated the IP & port number (of connection created by hw_server running on local computer) in the configuration. After launching the application project, the board could be programmed(just like we do on local computer).
