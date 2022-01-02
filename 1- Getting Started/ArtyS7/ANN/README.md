# Arduino Mega - ArtyS7: ANN

This tutorial is for people using an ArtyS7 with an Arduino Mega for ANNs. In this setup the Arduino would collect all sensor data readings and send them to the ArtyS7 via serial communication. The setup is minimal and is comprised of a PC, Arduino Mega, ArtyS7 and a small number of wires and resistors connecting the boards. 

## Overiew

![Full image showing PC connected to Arduino connected to ArtyS7](https://icii.io/wp-content/uploads/2022/01/ANNArtyS7.png)

Once setup is completed the Arduino will collect sensor data and use the ArtyS7 to perform the ANN inference. The PC is only used to read the result of the inference from the Arduino. This tutorial describes how to physically connect the system. 

Required components: 
- PC
- Arduino Mega
- ArtyS7
- USB cables
- Jumper wires
- Resistors




## Arduino Mega
![Image showing the initial connections to the Arduino](https://icii.io/wp-content/uploads/2022/01/Arduino-Mega-Connections.png)

Frist, we will connect the jumper wires and resistors to the Arduino. This will require 4 connections as show in the table below. Connect a jumper wire to each pin in the table. 
| Wire Name  | Pin   | Description | 
| -----      | ----- | ----- |
| Reset      | 4     | Raised hire at the very beginning of operations to initialize registers within the ArtyS7 |
| Arduino TX | 18    | Serial line where the Arduino writes data and commands to the ArtyS7 |
| Arduino RX | 19    | Serial line where the ArtyS7 writes the inference results to the Arduino |
| GND        | GND   | Ground connection, it is important to tie the grounds of the Arduino, ArtyS7 and resistors together |

### Resistor Voltage Divider
This setup requires a voltage divider to ensure that the communication voltages between the Arduino and ArtyS7 are at the correct levels. The Arduino outputs are at 5 V while the inputs to the ArtyS7 are at 3.3 V. If the voltage divider is not used it could damage the ArtyS7. Because Arduino RX is driven by the ArtyS7 it does not need a voltage divider. 
- Connections that **do** need voltage dividers: Reset, Arduino TX
- Connections that **do not** need voltage dividers: Arduino RX, GND

Create a voltage divider for Reset. Using a bread board, or other method, place a 1k &#x2126; resistor in series with a 2k &#x2126; resistor. Connect the disconnected end of the 2k &#x2126; resistor to GND. Now, connect the Reset jumper to the disconnected end of the 1k &#x2126; resistor. The voltage divider will be connected to the ArtyS7 in a future step. 

Create a voltage divider for Arduino RX following the same procedure as the one for Reset. 
 


## ArtyS7
![Image showing the Arduino connected to the ArtyS7](https://icii.io/wp-content/uploads/2022/01/Arduino-Connected-To-ArtyS7.png)
![Image showing a detailed depiction of the Arduino headers connected to the ArtyS7 PMOD header](https://icii.io/wp-content/uploads/2022/01/PMOD-To-Arduino.png)


## PC







### Step 1 - Download Vivado
Vivado is Xilinx's development and programming software suite and was initially released in 2012. For use with Icii, we recommend you download the Vivado Lab Solutions Verison. This version takes up much less space on your computer and will enable to program your FPGA. If you are interested in doing other FPGA development, you may need a different version of Vivad. 

Download and install your selected version of Vivado. You will need a free Xilinx account. 

Vivado download: https://www.xilinx.com/support/download.html 

### Step 2 - Install the Digilent Board Files
If you are using one of the Digilent development boards you will need to perform this step. You can follow Digilent's programming guide using the link below. 

Digilent board files instructions: https://digilent.com/reference/programmable-logic/guides/installing-vivado-and-sdk


