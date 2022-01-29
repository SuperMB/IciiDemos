# Arduino Mega - Nexys Video: CNN

This tutorial is for people using an Nexys Video with an Arduino Mega for CNNs. In this setup the Arduino would collect all sensor data readings and send them to the Nexys Video via serial communication. The setup is minimal and is comprised of a PC, Arduino Mega, Nexys Video, Camera, monitor, and a small number of wires and resistors connecting the boards. 

## Overiew

![Full image showing PC connected to Arduino connected to Nexys Video](https://icii.io/wp-content/uploads/2022/01/CNNNexysVideo.svg)
<p align="center">Image 1. Final system with PC connected to Arduino and Nexys Video.</p>

Once setup is completed the Camera will send its video to the Nexys Video via HDMI, the Nexys Video will mirror the incoming video on the monitor, and the Arduino talk to the Nexys Video to get the result of the most recent CNN inference. The PC is only used to read the result of the inference from the Arduino. This tutorial describes how to physically connect the system. 

Required components: 
- PC
- Arduino Mega
- Nexys Video
- Camera/HDMI video source
- Monitor to view the video
- USB cables
- Jumper wires
- Resistors


## Arduino Mega
![Image showing the initial connections to the Arduino](https://icii.io/wp-content/uploads/2022/01/Arduino-Mega-Connections.svg)
<p align="center">Image 2. Arduino connections</p>

Frist, we will connect the jumper wires and resistors to the Arduino. This will require 4 connections as show in the table below. Connect a jumper wire to each pin in the table. 

| Wire Name  | Pin   | Description | 
| -----      | ----- | ----- |
| Reset      | 4     | Raised hire at the very beginning of operations to initialize registers within the Nexys Video |
| Arduino TX | 18    | Serial line where the Arduino writes data and commands to the Nexys Video |
| Arduino RX | 19    | Serial line where the Nexys Video writes the inference results to the Arduino |
| GND        | GND   | Ground connection, it is important to tie the grounds of the Arduino, Nexys Video and resistors together |

### Resistor Voltage Divider
This setup requires a voltage divider to ensure that the communication voltages between the Arduino and Nexys Video are at the correct levels. The Arduino outputs are at 5 V while the inputs to the Nexys Video are at 3.3 V. If the voltage divider is not used it could damage the Nexys Video. Because Arduino RX is driven by the Nexys Video it does not need a voltage divider. 
- Connections that **do** need voltage dividers: Reset, Arduino TX
- Connections that **do not** need voltage dividers: Arduino RX, GND

Create a voltage divider for Reset. Using a breadboard, or other method, place a 1k &#x2126; resistor in series with a 2k &#x2126; resistor. Connect the disconnected end of the 2k &#x2126; resistor to GND. Now, connect the Reset jumper to the disconnected end of the 1k &#x2126; resistor. The voltage divider will be connected to the Nexys Video in a future step. 

Create a voltage divider for Arduino RX following the same procedure as the one for Reset. 
 


## Nexys Video
![Image showing the Arduino connected to the Nexys Video](https://icii.io/wp-content/uploads/2022/01/Arduino-Connected-To-NexysVideo.svg)
<p align="center">Image 3. Arduino connected to voltage divider and Nexys Video.</p>


![Image showing a detailed depiction of the Arduino headers connected to the Nexys Video Pmod header](https://icii.io/wp-content/uploads/2022/01/PMOD-To-Arduino.svg)
<p align="center">Image 4. Zoomed in connections between Arduino headers and Nexys Video Pmod.</p>

Next, we will connect the Arduino and voltage dividers to the Nexys Video. Image 3 shows the final connections between the two boards. Image 4 shows a more descriptive connection to the Nexys Video Pmod header. 

### Pmod Header
Pmod is a popular header used by Digilent (Nexys Video manufacturer). The Pmod headers can be used as generic IOs (inputs/outputs) or plug and play modules, such as cameras or sensors, provided by Digilent or other manufacturers. We will use the JA Pmod header for the Arduino - Nexys Video communication. More information on the Pmod header can be found in the [Nexys Video Reference Manual](https://digilent.com/reference/programmable-logic/arty-s7/reference-manual).

Each Pmod header is setup such that when looking the holes, the left most column inputs are both VCC and the second left most column inputs are both GND. This is reflected in Image 4. 

We will refer to the pin input locations on the Pmod header according to the layout below. Again, this assumes you are looking directly at the holes on the header.


| | Left  |  |  |  |  | Right |
| :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
| **Top**    | 6  | 5  | 4  | 3 | 2 | 1 |
| **Bottom** | 12 | 11 | 10 | 9 | 8 | 7 |

Respectively, jumpers for the Reset, Arduino TX, Arduino RX, and GND signals will be connected to the following Pmod pins.


| Wire Name  | Pin   |  
| -----      | ----- | 
| Reset      |  3    | 
| Arduino TX |  1    | 
| Arduino RX |  2    | 
| GND        |  5    | 



### Non-Voltage Divider Connections
First, we will connect the GND wire. Connect a jumper wire to the JA Pmod header, pin 5, and connect the jumper wire to the Arduino GND. This can be a direct connection with a single wire or it can be connected through a breadboard. This should tie the ground wires for the Arduino, Nexys Video, and voltage dividers together. 

Next, connect a jumper wire for the Arduino RX signal. Connect the jumper to the JA Pmod header, pin 2, and connect the jumper to pin 19 on the Arduino. Similarly, this can be connected directly or through a bread board.  

### Voltage Divider Connections
Now we will connect the Reset and Arduino TX signals using the voltage dividers we created previously. Starting with the Reset signal, connected a jumper wire to pin 3 on the JA Pmod header. Now, connect the other end to the node that connects the respective 1k &#x2126; and 2k &#x2126; resitors for the Reset signal. This should resemble the connection in Image 4. 

Similarly, for the Arduino TX signal, connect a jumper wire to pin 1 on the JA Pmod header. Connect the other end to the node that connects the respective 1k &#x2126; and 2k &#x2126; resitors for the Arduino TX signal. 

At this point, the Arduino and Nexys Video should be connected as shown in Image 3. 

## PC

![Full image showing PC connected to Arduino connected to Nexys Video](https://icii.io/wp-content/uploads/2022/01/CNNNexysVideo.svg)
<p align="center">Image 5. Final system with PC connected to Arduino and Nexys Video.</p>


The next step is to connect the Arduino and Nexys Video to your PC. Connect a USB cable to each using the respective cable type and connect them to your PC. The PC - Arduino connection will be used to program the Arduino and observe the results from the CNN inferences. The PC - Nexys Video connection will only be used to program the Nexys Video. Once programmed, the Nexys Video will function as expected on power up without a PC connection.

Finally, connect an HDMI cable to the camera / video source, and connect other end to the HDMI IN on the Nexys Video. Similarly, connect and HDMI cable from the HDMI OUT on the Nexys Video to the monitor. 

## Next Steps
Congratulations! You have now finished setting up the hardware. Click [Here](https://github.com/SuperMB/IciiDemos/tree/main/1-%20Getting%20Started/3-%20IciiBundle/) to continue the tutorial and learn how to use your Icii Bundle/Snowball. 