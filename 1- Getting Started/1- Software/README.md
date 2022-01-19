# Installing the Required Software
To use the associated hardware you will need to download software from the vendors to program the device. The respective software programs are:
- FPGA: Xilinx Vivado Lab Edition
- Arduino: Arduino IDE 


## Step 1 - Install Vivado Lab Edition
For use with Icii, we recommend downloading the Vivado Lab Edition Verison. This version takes up much less space on your computer and will enable to program your FPGA. Furthermore, we recommend version 2020.1 as this is what our tooling is currently tested with. 

First, install [Vivado 2020.1 Lab Edition](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html) by clicking [this link](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html), which should open the page below. 

![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-1.Smaller.png)

Then, click 2020.1 which should then expand.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-2.Smaller.png)

Scroll down until you see Vivado Lab Solutions - 2020.1. Click the download link for your operating system. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-3.4.Smaller.png)

This will take you to a sign in page. If you have a Xilinx account, sign in. If not, create one, it's free, and then you may have to repeat the previous steps.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-5.Smaller.png)

Fill in the required fields and click the Download button.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-6.2.Smaller.png)

This will download a file with a name similar to "Xilinx_Vivado_Lab_Win_2020.1_0602_1208.tar.gz". Extract the files. If you are running Windows, you may need to download a program such as [7-Zip](https://www.7-zip.org/). If you are unfamiliar with .tar.gz files, you may first extract the files, resulting in a .tar, and then extract the files from the .tar. 

Run the Vivado installer, the file "xsetup.exe". This will launch a window like the one below. If it asks you to install latest, hit continue to continue installing version 2020.1.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-7.Smaller.png)

Click Next.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-8.Smaller.png)

As with all software, you have to agree to Xilinx's terms to use the software. Click the 3 "I Agree" checkboxes, then click Next.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-9.Smaller.png)

One this screen, make sure to have Install Cable Drivers selected. This is required to be able to program your FPGA. You can choose whether to leave Enable WebTalk selected. Click Next.  
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-10.Smaller.png)

You can set the download location. We recommend leaving the defaults. If you change the path too much it may hinder future steps. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-11.Smaller.png)

Click Install. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-12.Smaller.png)

The installer will remain on a similar screen untill the installation is finished. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-13.Smaller.png)


<!-- ### Step 1.5 - Install the Digilent Board Files -->
<!-- If you are using one of the Digilent development boards you will need to perform this step. Digilent provides a good instructions, so follow their [Tutorial](https://digilent.com/reference/programmable-logic/guides/installing-vivado-and-sdk). -->

## Step 2 - Install the Arduino IDE

Next, install the Arduino IDE so that you can program your Arduino. Go to the [Arduino Download Page](https://www.arduino.cc/en/software). Click your respective operating system on the right side. This tutorial follows a Windows installation. Click "Win 7 and newer".
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-1.Smaller.png)

If you like, you may contribute to Arduino, otherwise click Just Download. This will download an installer file with a name similar to "arduino-1.8.19-windows.exe". 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-2.Smaller.png)

Run the installer that was just downloaded, it should open a window as seen below. It may ask you for permission to run the installer. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-3.Smaller.png)

We recommend leaving all of the defaults selected. Click Next. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-4.Smaller.png)

If you want, you may change the download location, but we recommend using the default. Click Install. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-5.Smaller.png)

The Arduino installer will now proceed to install the software. Let it continue until it finishes. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-6.Smaller.png)

Once the installer is finished, it will show Completed. Click Close. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Aruidno-7.Smaller.png)

## Next Steps
Congratulations! You have now finished installing the required software. Click [Here](https://github.com/SuperMB/IciiDemos/tree/main/1-%20Getting%20Started/2-%20Hardware/) to continue the tutorial and setup your hardware. 
