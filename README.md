SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 

 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

ENCODER

VERILOG CODE:

module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);
input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/784dbeb5-d80d-40f8-8a9a-391c3e67f04f)


LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)

DECODER

VERILOG CODE:

module decoder_3to8(
input [2:0] a,
output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule

OUT PUT:
![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/e46b6e39-dc67-40b1-b6a0-3e7a7d4ccdf1)


LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)

MULTIPLEXER:

VERILOG CODE:

module mux_8to1(in,sel,out);
input [7:0] in; 
input [2:0] sel;
output reg out;
always @(*)
begin
case (sel)
3'b000: out = in[0];
3'b001: out = in[1];
3'b010: out = in[2];
3'b011: out = in[3];
3'b100: out = in[4];
3'b101: out = in[5];
3'b110: out = in[6];
3'b111: out = in[7];
default: out = 1'bx;
endcase
end
endmodule

OUT PUTl:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/f18c61e6-072c-409e-bab6-6b8b0174e042)

LOGIC DIAGRAM:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/19bec669-c6a1-467a-bb18-5fe56289067d)

DEMULTIPLEXER:
VERILOG CODE:

module demux_1_to_8(d,s0,s1,s2,y0,y1,y2,y3,y4,y5,y6,y7);
input d,s0,s1,s2;
output y0,y1,y2,y3,y4,y5,y6,y7;
and g4(y0,d,~s0,~s1,~s2);
and g5(y1,d,~s0,~s1,s2);
and g6(y2,d,~s0,s1,~s2);
and g7(y3,d,~s0,s1,s2);
and g8(y4,d,s0,~s1,~s2);
and g9(y5,d,s0,~s1,s2);
and g10(y6,d,s0,s1,~s2);
and g11(y7,d,s0,s1,s2);
endmodule

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/22e307d9-f94a-4797-85da-f093ee2cf413)


LOGIC DAIGRAM:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/0cc274e8-6704-48a1-87a6-9a7ffc231fbb)

MAGNITUDE COMPARATOR:

VERILOG CODE:
module comparator(a,b,x,y,z);
input [3:0]a,b;
output reg x,y,z;
always@(a,b)
begin
if(a>b)
begin
x=1'b1;
y=1'b0;
z=1'b0;
end
else if(a<b)
begin
x=1'b0;
y=1'b1;
z=1'b0;
end
else
begin
x=1'b0;
y=1'b0;
z=1'b1;
end
end
endmodule

OUT PUT:

![image](https://github.com/Sandeep9347/VLSI-LAB-EXP-2/assets/160619092/32c1461f-0e76-4f47-bd7c-4d17a2828708)



  
PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

VERILOG CODE

   <<< TYPE YOUR VERILOG CODE >>>

OUTPUT WAVEFORM
 <<< PASTE YOUR OUTPUT WAVEFORM >>>

RESULT:
thus simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.1 was done and output verified successfully.


