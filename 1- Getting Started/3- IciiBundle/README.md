# Using Your Snowball
Once one of our Yetis translate your AI model into an FPGA design, they toss you a Snowball, packed with everything you need. The Snowball contains what you need to program your FPGA and Arduino.  First we will go over programming the FPGA and then the Arduino. 


## Programming your FPGA
FPGA programming can be complicated with lots of steps, and we don't want you to have to do that. Like everything, we think its important to keep things simple. Inside the Snowball you should see 2 folders, 1 named Arduino, 1 names FPGA. Open the FPGA Folder. Here, you should find 2 files. 
- IciiFpgaProgrammer.exe
- SomethingSomethingSomething.mcs

Open a Powershell window and navigate to your Snowball. Make sure the USB cable is plugged into your computer and the FPGA board. Then, enter the following command:

some text will print out

and after a few minutes, you are finished!

Cycle power to the FPGA board. Now, anytime you power on the FPGA board the desired functionality will automatically load onto the FPGA and you will be ready to use it. 

## Programming the Arduino
Programming your Arduino has only a few steps:
- Make sure the Arduino is connected to your PC with a USB cable.
- Click Tools > Board > and select Arduino Mega or Mega 2560
- Click Tools > Port > and make sure the Arduino port is selected. It should be something similar to ACM0. 
- Click the Right Arrow button in the top left to program!

## Using the Arduino Example
Launch the Arduino terminal. 

There are 3...ish commands that you can use with the Example: Initialize, Start#, Stop. 
- Intialize: This is the first command you must issue after powering on the FPGA. This will ensure that it is in a state ready to accept data. 
- Start#: This is more of a command set. For each possible class, you can call Start to begin emulating a detection for the class. For example:
    - Start0
    - Start1
- Stop: This stops the current detection stream

That's it! Have fun, we are excited for you journey into Source AI. 


# Digging Into the Aruidno Example (Not Required)
At this point, your Arduino - FPGA system should be successfully implementing you AI inference. This section is not required but will help you dig into the Arduino code. You will use the Arduino to collect data from sensors and send that data to the FPGA. Because of this, there is more flexibility in what you may want to do. To get you started, we provide a small example project tailored to your AI model. 

In the Snowball open the Arduino folder.

Next, open the Example folder.


You will see a handfull of .h and .cpp files. Don't worry about those, they are the structure to make communication with the FPGA board simple. Open the Arduino script provided, the Example.ino file. This should launch the Arduino IDE. 

The Example is designed to enable you to send a detection from your training/testing data, and it will modify inputs slighty for each detection. This is done to mimic how the system may be used in the wild. We will now go through each section of the Example.ini.

### Input for Example

```
//*********************************************************************************
//**************************** Input for Example **********************************
//*********************************************************************************
const int inputCount = 6;
bool detecting = false;

float dataValues[inputCount];
float initialDataValuesClass0[inputCount] = {
   2577.32, 1.00781, 52500,  134868000, 7656.25, 14062.5
};
float initialDataValuesClass1[inputCount] = {
  2577.115, 1.00781, 52500, 1978150000,    7500, 14648.4
};
```

inputCount defines the number of inputs into your ANN. 

detecting is set to true when you begin an example detection, and set to false when you tell it to Stop.

dataValues is populated with the values to send to the FPGA. 

initialDataValuesClass0 is an input vector that should be classified as 0 according to your data.

initialDataValuesClass1 is an input vector that should be classified as 1 according to your data.



### Implement OnResultReceived
```
//*********************************************************************************
//************************ Implement OnResultReceived *****************************
//*********************************************************************************

class TealeCommunicator : public QuantizedClassifierCommunicator
{
  public:
    TealeCommunicator()
    {
      /*Required*/ SetResetPin(4);
      /*Required*/ SetInputCount(inputCount);
      /*Required*/ SetOutputCount (2);    
    }
  
  protected:  
    /*Required*/ virtual void OnResultReceived()
    {
      //Call parent class to determine classification
      /*Required*/ QuantizedClassifierCommunicator::OnResultReceived();

      //Print inference result
      String resultString = 
          "Class:\t" + String(Classification) + 
          "\tConfidence:\t" + String(Confidence) + 
          "\tInference:\t" + String(SuccessfulInferences);
      for(int i = 0; i < OutputCount; i++)
          resultString += "\tClass " + String(i) + ":\t" + String(Classes[i]);
      Serial.println(resultString);  
      
      //For demo, alter input values slightly
      for(int i = 0; i < InputCount; i++)
        dataValues[i] += (int)((float)random(-1, 2) * 0.001 * (Maximums()[i] - Minimums()[i]));

      //For demo, if Stop has not been sent, send next detection to FPGA
      if(detecting)
        SendDetection(dataValues, inputCount);
    }
    
    /*Required*/ virtual float* Minimums() { return _minimums; }
    /*Required*/ virtual float* Maximums() { return _maximums; }
  
  private:
    /*Required*/ const float _minimums[6] = { 2577.115, 0.53418, -10000.0, 1301470.0, 6250.0, 1171.88 };
    /*Required*/ const float _maximums[6] = { 4561.817, 3.66016, 137500.0, 2045240000.0, 16093.8, 25195.3 };
};
TealeCommunicator tealeCommunicator = TealeCommunicator();
```
This block of code is what you need to implement to handle the result of the AI inference. First, let's talk about the boiler plate items.
- First, your custom class inherits from QuantizedClassifierCommunicator. 
- In the constructor, you must call SetRestPin, SetInputCount, and SetOutputCount to set the needed internal paramters.  
- Other required fields are the Minimums and Maximums at the bottom, also pulled from analyzing your training and testing data. 
- At the end of the block, create an instantiation of the class. 

It is also important to point out that all of the required components are tagged with /* Required */.

Now, let's focus on the OnResultReceived() function. This function overrides the virtual parent function and is called once the FPGA returns a result.
- First, we call the parent class's OnResultReceived using QuantizedClassifierCommunicator::OnResultReceived(); This puts the result into the Classes, Classification, and Confidence variables. 
- Then, for ease of use, we print the result to the terminal. 
- Next, we alter that input vector slightly for the example. 
- Finally, we send a new detection to the FPGA. 

In your own implementation, you will need to decide when and where to gather new sensor readings and send them to the FPGA. We will happily assist you on decide how to go about this. 

