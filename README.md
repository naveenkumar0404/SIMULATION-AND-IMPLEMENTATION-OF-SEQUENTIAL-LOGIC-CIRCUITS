# EXP.NO:04
# DATE:02/04/2024


# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

**AIM:**

 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

**APPARATUS REQUIRED:**

VIVADO 2023.1

**PROCEDURE:**

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

LOGIC DIAGRAM

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

CODE
```
module srff(s,r,clk,reset,q);
input s,r,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({s,r})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = 1'bx;
 default:q = ~q;
endcase
end 
end
endmodule
```
OUTPUT

![322170315-76dd3b2b-2552-4558-9989-02a238ad5a52](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/dfe87063-e285-4985-b482-9637df3ae56d)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

CODE

```
module jk_ff(j,k,clk,reset,q);
input j,k,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({j,k})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = ~q;
 default:q =1'b0;
endcase
end 
end
endmodule
```

OUTPUT

![322170505-da8fdddd-f458-4d50-b041-cdec899e433e](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/754d6a7b-3888-4fb7-acf0-ae0680dfa1f2)


T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

CODE

```
module tff(clk,rst,j,q);
input clk,rst,j;
output reg q;
always@(posedge clk)
begin
case(t)
1'b0:q=q;
1'b1:q=~q;
default=q=1'b0;
endcase
end
endmodule
```
OUTPUT

![322170538-39821533-3ed5-40d8-baff-361365b2a097](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/91412bd9-30d7-4c37-b6ed-64c61489f9b1)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

CODE

```
module dff(clk,rst,d,q);
input clk,rst,d;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
OUTPUT
![322170602-c9ddaf50-4871-434f-95f3-4d07d4237a7b](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/dd3396d0-affa-4f7f-aa6b-3ea824d7b564)




COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

UPDOWNCOUNTER

![320875970-dd12585a-157f-4b6f-a0c3-b421bb52434c](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/20920312-1c6e-40e3-984c-2af75b726b5f)


CODE
```
module updown(clk,rst,up_down,count);
input clk,rst,up_down;
output reg[3:0]count;
always@(posedge clk)
begin
if(rst==1)
count <= 4'b0000;
else if (up_down == 1'b1)
count <= count + 1'b1;
else
count <= count-1'b1;
end
endmodule
```

OUTPUT

![323980011-f8568576-1d56-41f5-9d37-3d499c208bb1](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/08d84db9-7847-4a03-a915-1fad58ce7f0f)

MOD10COUNTER

![320876746-3a4a4da2-7488-411d-8ea5-2e57c4fd942f](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/1f38505d-d423-4ec0-a7f4-6fc881ab5304)


CODE
```
module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule
```

OUTPUT

![323981063-5c6e7959-bd3b-4f7d-b187-32961ef828f1](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/1421c91c-e4f6-4602-babc-0e1a33af170e)

RIPPLECARRYCOUNTER

![320960585-3ac04a13-47b6-4664-890d-25133409319b](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/0edfd64b-91fc-42ff-a937-e240a330e1f4)

![320960626-a2e3e352-fd4f-4e4a-b2c9-3311cced9743](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/6b447aaa-5950-4e92-bfdd-28a575502a40)

CODE
```
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule
```

OUTPUT

![323981592-f761bce4-93f5-4813-aaa0-5bccadc60b6d](https://github.com/naveenkumar0404/VLSI-LAB-EXP-04/assets/127510390/37082f54-7855-4759-a7db-f594fe352043)

**RESULT:**

Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.

