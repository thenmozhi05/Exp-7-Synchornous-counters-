# DEVELOPED BY: thenmozhi p
# REG NO: 23005024

##  Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
## procedure:
1.Create a New Project:
Open Quartus and create a new project by selecting "File" > "New Project Wizard."
Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).
2.Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.
⦁	Write the Combinational Logic Code:

Open the newly created Verilog or VHDL file and write the code for your combinational logic.
3.Compile the Project:
To compile the project, click on "Processing" > "Start Compilation" in the menu.
Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.
4.Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
Review and fix any issues in your code if necessary.
View the RTL diagram.
5.Verification:
Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.

Give the Input Combinations according to the Truth Table and then simulate the Output Waveform.


## UP COUNTER 

## program:
module upCounters(clk, A);

input clk;

output reg [2:0]A;

always @(posedge clk)

begin

	A[2]=(((A[0])&(A[1]))^A[2]);
 
	A[1]=(A[0])^A[1];
 
	A[0]=A[0]^1;
 
end

endmodule
## RTL REALIZATION:
![WhatsApp Image 2023-12-20 at 20 56 29_7dcabd64](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/c283eff0-f438-409e-a830-d3f19628f97e)
## TRUTH TABLE:

![Screenshot 2023-12-20 214435](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/c2b57cce-4b4d-426b-aa7a-1241118a14cf)

 ## WAVEFORM:
 
 ![Screenshot 2023-12-20 215157](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/d2839b5b-07e0-4c88-b78e-c36641f63b8a)
 ## DOWN COUNTER:
 module downCounters(clk,A);
 
input clk;

output reg [2:0]A;

always @(posedge clk)

begin

	A[2]=(((~A[0])&(~A[1]))^A[2]);
 
	A[1]=(~A[0])^A[1];
 
	A[0]=1^A[0];
 
end 

endmodule
## RTL REALIZATION:
![WhatsApp Image 2023-12-20 at 20 56 49_5d03bff0](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/53eb74d4-fa80-492e-9d7a-813135622b79)
## TRUTH TABLE:
![image](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/e72783bc-a5a2-4f57-b2d2-a06399205dba)
## WAVEFORM :
![image](https://github.com/23011258/Exp-7-Synchornous-counters-/assets/139842204/75cbd884-cb5e-4d59-a459-f7f20073e15f)

## RESULT:
By this we have verified the truth table of 4-bit up-counter using verilog.
