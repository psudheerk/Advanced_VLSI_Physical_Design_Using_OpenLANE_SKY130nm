# Advanced_VLSI_Physical_Design_Using_OpenLANE_SKY130nm
<img width="897" alt="Banner" src="https://user-images.githubusercontent.com/100553237/183464151-bc5b8a77-4c62-48d0-a80c-607d3da587d4.png">

* **RTL - GDSII flow**<br>
We define the specification of the design using the Hardware Description Language(HDL) called verilog and the timing constraints are given in the form of standard design constraints(SDC) including the frequency of the design and input&output delay.


 
* **Synthesis**<br>
Synthesis is the design step in which the RTL description of the design is converted to gate level netlist so that it can be implemented on a chip.

* **PHYSICAL DESIGN**<br>
Physical design is the process of implementing the design taking synthesized netlist and standard cell libraries as the inputs and producing the 
GDSII file which is given as an input to the foundry so as to manufacture it.<br>
Physical design consists of <br>
a) Floorplan<br>
b) Powerplan<br>
c) Placement<br>
d) Clock tree synthesis<br>
e) Routing<br>
f) Physical Verification <br>
g) Timing ECO

* **Design**
For this project, I have chosen the project called picoRV32a, which is a CPU core which implements the RISC-V instruction set.

* **Synthesis Flow**<br>
Inputs<br>
a) RTL behavioural netlist<br>
b) SDC file<br>

Outputs<br>
a) Gate level netlist

After giving the inputs of a RTL bevarioural netlist and SDC file as an input, the flow of commands looks like below, <br>
```
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
run_synthesis
```
In the results that follow, we calculate the total flop ratio which is like below
```
total no of flip flops  : 1613
total no of cells       : 14876
total flop ratio        : 10.86%
```
The `yosys` tool along with the `abc` does the synthesizing and mapping the libraries and also the netlist would be optimized to improve the timing in the 
initial stage itself and afte the process the WNS(worst negative slack) and TNS(total negative slack) would be displayed on the command terminal and also can be checked from the `reports/synthesis` directory.

The initial timing report of my design is as follows
```
tns -759.46
wns -24.89
```





