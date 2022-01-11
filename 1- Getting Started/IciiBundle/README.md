# Installing the Required Software
To use the associated hardware you will need to download software from the vendors to program the device. The respective software programs are:
- FPGA: Xilinx Vivado Lab Edition
- Arduino: Arduino IDE 


## Step 1 - Install Vivado Lab Edition
For use with Icii, we recommend downloading the Vivado Lab Edition Verison. This version takes up much less space on your computer and will enable to program your FPGA. Furthermore, we recommend version 2020.1 as this is what our tooling is currently tested with. 

First, install [Vivado 2020.1 Lab Edition](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html) by clicking [this link](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html), which should open the page below. 

![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-1.png)

Then, click 2020.1 which should then expand.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-2.png)

Scroll down until you see Vivado Lab Solutions - 2020.1. Click the download link for your operating system. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-3.4.png)

This will take you to a sign in page. If you have a Xilinx account, sign in. If not, create one, it's free, and then you may have to repeat the previous steps.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-5.png)

Fill in the required fields and click the Download button.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-6.2.png)

This will download a file with a name similar to "Xilinx_Vivado_Lab_Win_2020.1_0602_1208.tar.gz". Extract the files. If you are running Windows, you may need to download a program such as [7-Zip](https://www.7-zip.org/). If you are unfamiliar with .tar.gz files, you may first extract the files, resulting in a .tar, and then extract the files from the .tar. 

Run the Vivado installer, the file "xsetup.exe". This will launch a window like the one below. If it asks you to install latest, hit continue to continue installing version 2020.1.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-7.png)

Click Next.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-8.png)

As with all software, you have to agree to Xilinx's terms to use the software. Click the 3 "I Agree" checkboxes, then click Next.
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-9.png)

One this screen, make sure to have Install Cable Drivers selected. This is required to be able to program your FPGA. You can choose whether to leave Enable WebTalk selected. Click Next.  
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-10.png)

You can set the download location. We recommend leaving the defaults. If you change the path too much it may hinder future steps. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-11-1.png)

Click Install. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-12.png)

The installer will remain on a similar screen untill the installation is finished. 
![Vivado archive download page](https://icii.io/wp-content/uploads/2022/01/Download-Vivado-13.png)





## Step 2 - Install the Digilent Board Files
If you are using one of the Digilent development boards you will need to perform this step. You can follow Digilent's programming guide using the link below. 

Digilent board files instructions: https://digilent.com/reference/programmable-logic/guides/installing-vivado-and-sdk