
## NAME: thenmozhi p
## Register number:23005024 
# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 3 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### Procedure
1)Create a New Project:

   * Open Quartus and create a new project by selecting "File" > "New Project Wizard."
   * Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).
     
 2)Create a New Design File:

  * Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
  * Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.
    
 3)Write the Combinational Logic Code:

  * Open the newly created Verilog or VHDL file and write the code for your combinational logic.
    
 4)Compile the Project:

  * To compile the project, click on "Processing" > "Start Compilation" in the menu.
  * Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.
    
 5)Analyze and Fix Errors:

  * If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
  * Review and fix any issues in your code if necessary.
  * View the RTL diagram.
    
 6)Verification:

  * Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
  * Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.
  * Give the Input Combinations according to the Truth Table and then simulate the Output Waveform.


## UP COUNTER 
The counter is a digital sequential circuit and here it is a 3 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

## PROGRAM:
```
module up_counter(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=(q1&q2)^q3;
q2=q1^q2;
q1=1^q1;
end 
endmodule

```
## RTL LOGIC FOR UP COUNTER

![293361869-a03a9147-4071-4d8c-b1bb-c94baaacfe25](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/3b61dc51-6b60-4f11-b208-67f78588976e)
## TRUTH TABLE
![293361897-0fad4afb-aff2-4a62-8494-e081757ba1ca](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/af9c656e-12f2-40b2-a4ef-2d069a48a293)

## TIMING DIAGRAM FOR UP COUNTER
![293361908-1fa2cb7e-3c27-4c4e-a7be-71bfbca01bb6](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/cfe91c9f-79dc-435b-8f5f-8ecb7ec465d4)

## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 3-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.


3-bit Count Down Counter


### PROGRAM 
```
module COUNTER(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=((~q2)&(~q1))^q3;
q2=(~q1)^q2;
q1=1^q1;
end
endmodule
```
### RTL LOGIC  DOWN COUNTER  


![293361964-aea0bb57-ab87-4549-9720-c26f35609f2d](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/244f8309-9c9b-4401-95a5-c9846fb4d440)

### TIMING DIGRAMS FOR COUNTER  



![293361994-169f6ffa-5e86-4212-9451-25c5981e77b0](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/1ff173ce-f29c-424b-8174-3833cf38a8c5)

### TRUTH TABLE 

![293361980-e6ff8e0f-9248-4fa0-b05f-cbe39e102dcf](https://github.com/Himavath08/Exp-7-Synchornous-counters-/assets/139110631/40f97132-fa15-4669-b02e-61eb690ac7d8)


### RESULTS 
By this we have verified the truth table of 3-bit up-counter using verilog.



