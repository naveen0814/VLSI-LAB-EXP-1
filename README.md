# SIMULATION OF LOGICGATES , ADDERS , SUBRACTORS USING VIVADO.
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado.

APPARATUS REQUIRED: Vivado 2023.1

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. 
STEP:2 Select the device family, device, package and speed. 
STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. 
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. 
STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. 
STEP:11 Load the Bit file into the SPARTAN 6 FPGA 
STEP:12 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)





VERILOG CODE:

Logic Gates:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT:
LogicGates:
![Screenshot_20240304_134535](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/26ed6de9-745c-4d28-baa3-8de981f17084)
![Screenshot_20240401_132931](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/b2269c7e-0298-4b93-a259-f32384ac553d)

Half Adder:
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry; 
or(sum,a,b);
and(carry,a,b);
endmodule
```
OUTPUT:
HalfAdder:
![image](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/f061c9b0-2c32-489f-9990-9c6a7af013aa)
![image](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/fcb60359-6ab6-4f1d-8cf6-802fa23595c2)

Full adder:
```
module fa_ha(a,b,c,sum,cout);
input a,b,c;
output sum,cout;
wire wl, w2, w3, w4, w5;
xor x1(w1,a,b);
xor x2 (sum,w1,c) ;
and al(w2,a,b) ;
and a2(w3,b,c);
and a3(w4,a,c) ;
or o1(w5,w2,w3) ;
or o2(cout,w5,w4) ;
endmodule
```
OUTPUT:
FullAdder:
![image](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/46df7b9f-56fa-4f73-a653-d0049fa8557c)
![Screenshot_20240401_133333](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/0444f83d-1097-478e-be69-9198c4690a08)

Half Subtractor:
```
module halfsubtractor( D,Bo,A,B);
input A,B;
output D,Bo;
wire w1;
xor (D,A,B);
not (w1,B);
and (Bo,B,w1);
endmodule
```
OUTPUT:
HalfSubractor:
![image](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/314eebe8-1a90-4d24-a9d5-8c3b1be1facf)
![Screenshot_20240401_132342](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/2fcf3e81-40d4-4e3f-886d-089dcf495a63)

Full Subtractor:
```
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
```
OUTPUT:
FullSubractor:
![Screenshot_20240315_135703](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/c97ce04b-bdd9-4373-bf91-d835e93ac7b3)
![Screenshot_20240401_131933](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/ea219104-7762-4f7c-b77d-61f6553f79eb)

4 Bit Ripple Carry Adder
```
module rippe_adder(S, Cout, X, Y,Cin);
 input [3:0] X, Y;
 input Cin;
 output [3:0] S;
 output Cout;
 wire w1, w2, w3;
 fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;
  wire w1,w2,w3;
  xor G1(w1, X, Y);
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
```
OUTPUT:
4 Bit Ripple Carry Adder:
![Screenshot_20240315_135322](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/7614d204-24c5-4e14-a5e0-0e680c0c5439)
![Screenshot_20240401_133512](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/4b1c23b4-0e1c-40bd-b81a-37e2245267b8)


8 Bit Ripple Carry Adder
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
OUTPUT:
8 Bit Ripple Carry Adder:
![Screenshot_20240401_134309](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/4a80404a-bdb5-4dc4-acdf-853b2383ebc4)
![Screenshot_20240401_134126](https://github.com/naveen0814/VLSI-LAB-EXP-1/assets/161302822/8d615aa2-036d-433b-87a6-577169711aba)


RESULT:
Thus the simulation and synthesis of Logic Gates, Adders and Subtractors using Vivado are successfully completed.
