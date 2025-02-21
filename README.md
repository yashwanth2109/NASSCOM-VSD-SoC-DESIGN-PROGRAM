DAY 1: INCEPTION OF OPEN-SOURCE EDA, OPENLANE AND SKY130 PDK

Introduction to  QFN-48 Chip, Pads, Core, Die, Macros & IPs

QFN-48 Package
The QFN-48 (Quad Flat No-lead, 48-pin) package is a compact, surface-mount IC package designed for high-performance applications with efficient thermal dissipation and low parasitic effects. It features 48 connection pads around its edges and a central exposed pad for improved heat dissipation, making it ideal for space-constrained designs.
Core:
The core is the central region of the chip where the main logic components are placed. It houses combinational circuits, standard cells, hard and soft IPs, and interconnections that define the chip’s functionality.
Die :
The die is the physical silicon area that contains both the core and the I/O pads. Multiple dies are fabricated on a single wafer, which is later cut into individual chips for packaging.
Pads :
I/O pads serve as the interface between the core and external connections, enabling communication with other components. These pads include input, output, and power pads, and are typically surrounded by pad cells that facilitate external bonding.
![image](https://github.com/user-attachments/assets/9274433c-25e9-41db-9354-bb3cb838af80)
Macros and Foundry Ips
Macros are pre-designed functional blocks used within an integrated circuit (IC) to optimize design efficiency. They can be hard macros (pre-placed and routed, such as memory blocks or analog components) or soft macros (synthesizable and flexible, like digital logic modules). Foundry IPs (Intellectual Properties) are pre-verified circuit designs provided by semiconductor foundries to assist in chip design. These can include standard cells, memory compilers, I/O libraries, PLLs, ADCs, DACs, and high-speed interfaces.

![image](https://github.com/user-attachments/assets/e71b5b27-123e-4825-ab16-ad237f697575)

Overview of RISC-V Processor
The Instruction Set Architecture (ISA) defines how software communicates with hardware, acting as the intermediary between the code we write and the machine's operations. While high-level programming languages like C and Java are used to develop applications, machines can't understand them directly. Instead, ISA enables the translation of programs from assembly language to machine code that the hardware can execute. The RISC-V ISA is the latest open-source architecture designed for this purpose, providing a simple, efficient, and flexible instruction set that allows for customization and optimization in processor  design. 
![image](https://github.com/user-attachments/assets/d034a27a-7fe8-44c8-9a4a-50ef9401a9b9)
Software to Hardware
In everyday use, we interact with application software (like apps) to perform tasks, but there’s a process happening behind the scenes to bridge the gap between the software and the hardware. This bridge is provided by system software, which sits between the applications and the hardware, translating software instructions into a format that the hardware can process—binary code.
System software involves: 
![image](https://github.com/user-attachments/assets/e528f03d-af35-440e-97de-815930997c0e)

Operating System (OS):
The OS manages core functions like input/output, memory management, and system-level tasks. It translates application requests into higher-level code, often in languages like C, C++, or Java, that the system can handle.
Compiler:
The compiler takes this code and converts it into machine-readable instructions, often creating executable files (e.g., .exe), which are tailored for the specific hardware.
Assembler:
The assembler further processes these instructions, turning them into binary code, the only language that the hardware can directly understand and execute to perform the necessary operations.
ASIC design flow
 ![image](https://github.com/user-attachments/assets/b1c5fdbc-07e0-44a0-9615-87d3dc7371de)

ASIC design is a complex process that involves a series of steps to transform a design from Register Transfer Level (RTL) into the final GDSII layout file. The design flow integrates various tools and methodologies to ensure the final chip meets performance, area, and power requirements.

Synthesis:
The process where RTL code is converted into a gate-level netlist using a set of Standard Cell Libraries (SCLs), which defines the logic gates and their interconnections.
Floorplanning:
This step involves the arrangement of large functional blocks or macros on the chip layout and planning the power distribution network, which ensures efficient power delivery throughout the chip.
Placement:
In this phase, the individual cells and macros are positioned on the chip, both globally and with detailed adjustments, optimizing for area and performance.
Clock Tree Synthesis (CTS):
CTS aims to balance clock signal arrival times across the entire chip, minimizing clock skew and ensuring synchronous operation of all parts of the chip.
Routing:
The routing process connects the placed cells and macros using metal layers (e.g., SkyWater PDK uses up to 6 metal layers) to form the necessary interconnections between the logic blocks.
Sign-Off Checks:
Design Rule Checking (DRC): Verifies that the physical design adheres to the foundry’s manufacturing rules, ensuring manufacturability.
Layout vs. Schematic (LVS): Compares the layout with the gate-level netlist to ensure there are no discrepancies.
Static Timing Analysis (STA): Analyzes the timing of signals across the design to ensure the chip meets the required timing constraints and operates reliably at high speeds.


To successfully design an open-source digital ASIC, a few fundamental elements are essential: 
![image](https://github.com/user-attachments/assets/15ab75ee-1072-49f7-b718-b45815028edd)

RTL Designs
Register-Transfer Level (RTL) design is a foundational stage in the VLSI design process, where the functionality of digital circuits is described in terms of data flow between registers and the logical operations performed on that data. It serves as the blueprint for the digital behavior of the ASIC, specifying how data is transferred and manipulated within the circuit.
EDA Tools
Electronic Design Automation (EDA) tools are specialized software used to design, simulate, and verify integrated circuits (ICs). These tools help engineers test the functionality, timing, and performance of an IC, ensuring the design meets all required specifications, including power, area, and speed.
PDK Data
A Process Design Kit (PDK) provides the necessary files and data to model the manufacturing process used in IC design. It includes:
Design Rules for fabrication, which help ensure the layout complies with manufacturing limitations (e.g., DRC, LVS, etc).
Device Models to simulate the behavior of various components.
Digital Standard Cell Libraries for logic functions, and I/O Libraries for interfacing with external systems. These elements guide the design and ensure that the resulting ASIC can be manufactured reliably.
Introduction to OpenLANE and Strive chipsets
OpenLANE is an open-source ASIC design flow that provides a comprehensive toolchain for digital design, from RTL to GDSII, supporting custom chip development. It integrates several EDA tools for synthesis, placement, routing, and verification. It is a tape-out-hardened flow that addresses two main use cases: hardening a macro and integrating a System-on-a-Chip (SoC). It was used successfully to tape out a family of RISC-V based SoCs known as “striVe”.
 
![image](https://github.com/user-attachments/assets/d3147fb0-546f-4acf-afb3-e4d4f9a2d194)

StriVe chipsets are customizable, energy-efficient processors designed for specialized applications, focusing on low-power and high-performance computing. They leverage open-source frameworks like OpenLane to enable rapid prototyping and development of ASICs.


The observation of day 1:
To setup the directory for running synthesis
Run docker and flow.tcl file in interactive mode to open the bash interface
To Perform synthesis of the design picorv32a and analyze the flop ratio 

Set up the directory to the OpenLANE flow 
  cd Desktop/work/tools/openlane_working_dir/openlane

Run docker to open bash
  $ docker

Start OpenLANE in interactive mode
  ./flow.tcl -interactive

Load the required openlane packages with the version 0.9
  %package require openlane 0.9

Create the design picorv32a for synthesis
  prep -design picorv32a


![image](https://github.com/user-attachments/assets/1a9733eb-b980-4464-8852-90663540d0f9)


Run the synthesis:
run_synthesis


![image](https://github.com/user-attachments/assets/d921233c-5b0f-4aee-9401-63fc89e86df4)



![image](https://github.com/user-attachments/assets/da07cf04-52f7-440c-abca-98d470b8af68)


After completion of the synthesis, navigate to the yosys file to calculate the flop ration. The path of the yosys file is given below
 cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/(date)/reports/synthesis: less 1-yosys_4.stat.rpt


![image](https://github.com/user-attachments/assets/33aa099f-21ca-4c09-a9f6-220b2c86b55e)


The count of flip-flops is given by 'sky130_fd_sc_hd__dfxtp_2' 

Count of flip-flops: 1613

Number of cells: 14876

Flop Ratio = (Number of Flip-Flops) / (Total Number of Cells)

Flop ratio = 1613/14876 = 0.1084 [10.84%]


![image](https://github.com/user-attachments/assets/ec56ea60-8d68-4504-a8de-b057069deab7)



![image](https://github.com/user-attachments/assets/287659a0-4de0-41e7-9637-861f8de8cd4a)


DAY 2: Good floorplan VS bad floor plan and introduction to library cells

![image](https://github.com/user-attachments/assets/52ab8b90-8a07-48ad-8bca-f182b3500ef2)

 
![image](https://github.com/user-attachments/assets/d670d3dc-0ac8-4d38-af4c-2f648939a4fa)

![image](https://github.com/user-attachments/assets/2f45e358-ac22-46c8-9803-40c43d8dcc33)

Utilization Factor:
The Utilization Factor is the ratio of the area occupied by the netlist to the total available core area. For an optimized FloorPlan, the Utilization Factor should be less than 1. If it reaches 1, there won’t be any extra space for adding additional logic, making the FloorPlan 100% utilized.
Utilization Factor = Area occupied by netlist / Total core area
Aspect Ratio:
The Aspect Ratio represents the proportion between the height and width of the core. A core with an aspect ratio of 1 forms a square, whereas any other value results in a rectangular shape.
Aspect Ratio = Height of the core / Width of the core

![image](https://github.com/user-attachments/assets/853a631e-3570-4149-8f76-a6f1d4455d01)

In this case,
Utilization Factor = (4 x 1 sq. unit)/(2 unit x 2 unit) = 1
Hence, the core area is 100% utilized by the netlist.
Aspect Rtio = (2 unit)/(2 unit) = 1
Hence, the core has a square shape.
​
Now, after adding pre-placed cells, decoupling capacitors, power planning and pin Placement:

![image](https://github.com/user-attachments/assets/b7f8363a-c03d-4a89-aa19-337e92773a84)

Running Floorplan using OpenLANE:
The objectives of this section are to

 Define and run the floorplan 
 In OpenLANE
Review the floorplan output files and calculate the die area
Review the floorplan and placement in Magic
Perform congestion-aware placement using RePlAcE

Run the floorplan of the design picorv32a using the below command 

run_floorplan 


![image](https://github.com/user-attachments/assets/bfecdaf3-a272-4b50-b175-989e8f8a3be0)


Navigate to the results folder of the run (date) and inspect the picorv32a.floorplan.def


![image](https://github.com/user-attachments/assets/0c564380-12fa-427c-96e3-67727f89819d)


Analyse the width and height of the die area

Die width = 660685 d.u. = 660.685 microns  
Die height  671405 d.u. = 671.405 microns
Die area = Die width x Die Height =  660.685 microns x  671.405 microns = 443587.212425 square microns


![image](https://github.com/user-attachments/assets/1f51ce3b-cf8b-4b0f-9e6a-c7099eb83267)

View the floor plan in magic. Type the command given below :
   $ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &


![image](https://github.com/user-attachments/assets/a7b815d7-72b9-40f2-b6be-30a2c5d3d48c)


![image](https://github.com/user-attachments/assets/ed3e1510-11b7-466d-a281-a93b8d82cab1)


Once Magic opens, hitting S allows to select and inspect cells at different zoom levels (Z to zoom) and (shift+z to zoom out) Press v to align it to the center


![image](https://github.com/user-attachments/assets/c1f3b97d-9812-4fc2-8454-51c81ac684de)


In the 'tkcon' window, type what to display detailed information about the cell.


![image](https://github.com/user-attachments/assets/21d04aaf-1351-43fb-9e72-3f99e197a50e)


After viewing the floorplan close the magic file and run the placement 
run_placement 


![image](https://github.com/user-attachments/assets/e67d5d46-031d-4181-927e-4ae1b1868845)

Same as floorplan review, thereview the placement results in the design file’s latest run.

![image](https://github.com/user-attachments/assets/9f0926d4-acc1-408a-b81d-99af783c272c)

Open the file in magic using the below command:

 $ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![image](https://github.com/user-attachments/assets/5fcff4ef-d4b5-42c6-bc75-461846ff9cb1)



![image](https://github.com/user-attachments/assets/1307421b-88eb-490c-a7b6-837f7400d319)


In the placement process, each sigle cell (eg. Inverter) from the library has specific design flow that are classified into three different parts:
Inputs
PDKs
DRC and LVS rules
SPICE models
Library & User-defined specs
Design Steps
Circuit design
Layout Design
Characterization using GUNA
Outputs
CDL (Circuit Description Language)
GDSII
LEF (Library Exchange Format)
SPICE extracted netlist
Timing, Noise, and Power Libraries

Typical Characterization flow for a CMOS inverter circuit:
Reading model files (eg. PMOS or NMOS models).
Read extracted SPICE netlist.
Recognize the behaviour of the buffer.
Read sub-circuits of the inverter.
Attach necessary power sources.
Apply the stimulus to the characterization setup.
Provide necessary output load capacitance.
Provide necessary simulation command (eg., .tran or .dc).
Feed in the configuration file to GUNA software which will generate the timing, noise, power, .libs, etc models.

Timing Characterization in VLSI Design:
Timing characterization in VLSI design refers to the process of analyzing and modeling the behavior of a standard cell or a circuit concerning signal propagation delays, transition times (slew), and setup/hold constraints. It helps in generating timing libraries (e.g., Liberty .lib files) used for Static Timing Analysis (STA).

Key Timing Parameters:
Timing Threshold: These are predefined voltage levels (expressed as a percentage of supply voltage, VDD) used to measure delays and transitions in a digital circuit.
Propagation Delay: The time it takes for a signal transition to travel from the input to the output of a gate. It is measured between the same voltage thresholds on input and output, typically from 50% of input swing to 50% of output swing.
Slew Rate (Transition Time): The time taken for a signal to transition between two voltage thresholds.
Slew Low Rise Threshold (slew_low_rise_thr): The lower voltage threshold used to measure the rise transition time (e.g., 20% of VDD).
Slew High Rise Threshold (slew_high_rise_thr): The upper voltage threshold for rise time measurement (e.g., 80% of VDD).
Slew Low Fall Threshold (slew_low_fall_thr): The lower voltage threshold for fall time measurement (e.g., 20% of VDD).
Slew High Fall Threshold (slew_high_fall_thr): The upper voltage threshold for fall time measurement (e.g., 80% of VDD).
Input Rise Threshold (in_rise_thr): The voltage threshold used to measure rising transitions at the input.
Input Low Threshold (in_low_thr): The voltage threshold used to measure falling transitions at the input.
Output Rise Threshold (out_rise_thr): The voltage threshold used to measure rising transitions at the output.
Output Low Threshold (out_low_thr): The voltage threshold used to measure falling transitions at the output.















LAB DAY 3: Design library cell using Magic Layout and ngspice characterization
 
The objectives of this section are the following:
 
To analyze different placement modes with Magic tool
Clone CMOS inverter standard cell design from github repository 
Explore the inverter layout in Magic 
Extraction and adjustment  of CMOS inverter SPICE files from Magic 
CMOS inverter characterization with ngspice 
Sky130 Tech File Labs


The placement of the I/O pins are controlled by the value of FP_IO_MODE. 
Set the value of FP_IO_MODE to 2 and analyze the placement


![image](https://github.com/user-attachments/assets/e122a6de-2eee-4f31-a754-6f48e0eed27b)



![image](https://github.com/user-attachments/assets/972581bc-eca6-4b62-a068-94183f120d86)


Clone the CMOS inverter standard design in the openlane folder from the github repository using the below command:
git clone https://github.com/nickson-jose/vsdstdcelldesign.git

Observe the presence of a new folder (vsdstdcelldesign) in the openlane folder


![image](https://github.com/user-attachments/assets/2330b0d3-f239-47d5-b571-822f1b4c0e9f)


Sky130A.tech file is copied to the new folder (vsdstdcelldesign) using the below commands

cd Desktop/work/tools/openlane_working_dir./pdks/sky130/A/libs.tech/magic/ 

sky130A.tech/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/

Now we navigate to the folder which is cloned from the github to check whether the Sky130A.tech tile is copied

Run the Magic tool 
magic -T sky130A.tech sky_inv.mag &


![image](https://github.com/user-attachments/assets/3ebfdf48-a23e-408d-b8e0-185161404962)



![image](https://github.com/user-attachments/assets/45526fd6-94e5-48c7-bf33-9363297a9957)



![image](https://github.com/user-attachments/assets/42811257-76d6-4afd-8b1b-a40c6b9ffb7b)



We observe the following in the CMOS inverter layout

Connectivity of the drains of p-channel and n-channel MOSFETs to the output
Connectivity of the source of the p-channel MOSFET to VPWR
Connectivity of the source of the p-channel MOSFET to VPWR:

Now lets extract the CMOS inverter files from Magic
Open the tkcon window and run the below commands to extract the file:
extract all
After “extract all” command is executed there will be a file (sky130_inv.ext) created in vsdstdcelldesign folder

ext2spice cthresh 0 rthresh 0


![image](https://github.com/user-attachments/assets/0d13f088-73c6-4211-ac54-c69ef28e2407)



![image](https://github.com/user-attachments/assets/d8b204a4-fe29-49ca-9bfd-95111fa3abc6)


After “ext2spice cthresh 0 rthresh 0” command is executed there will be a file (sky130_inv.spice) created in vsdstdcelldesign folder


![image](https://github.com/user-attachments/assets/b0a1bf98-0c4c-47eb-b061-4558ad72a20c)


Observe the create spice file and edit the file to perform changes:
Correct the scale 
Include pshort and nshort MOSFETs lib models
Specify the Transient analysis

![image](https://github.com/user-attachments/assets/146a31df-4937-41da-810a-937bfd536cda)


Run the sky130_inv.spice in ngspice
Ngspice sky130_inv.spice

Plot the axis of the output:
ngspice 1 -> plt y vs time a


![image](https://github.com/user-attachments/assets/97d919ba-ac8a-4bf5-8c5e-0340f231f833)

![image](https://github.com/user-attachments/assets/ffa59c5e-4315-4ce6-ba91-afdb66228f60)



From this plot we can calculate various parameters related to timings and delays of the CMOS inverter characteristics.

Characterizing the parameters:
Rise Time: The time taken for the output waveform to transition from 20% to 80% of its maximum value.
Using data points:
x0 = 2.18257e-09, y0 = 0.66
x1 = 2.24684e-09, y1 = 2.64
Rise time = x1 - x0 = 0.06427 ns

Fall Time: The time taken for the output waveform to transition from 80% to 20% of its maximum value.
Using data points:
x0 = 4.07995e-09, y0 = 2.64
x1 = 4.09524e-09, y1 = 0.66
Fall time = x1 - x0 = 0.01529 ns

Propagation Delay: The time taken for a 50% transition at the output(low to high) corresponding to a 50% transition at the input(high to low).
Using data points:
x0 = 2.21153e-09, y0 = 1.65018
x1 = 2.14988e-09, y1 = 1.65018
Propagation delay = x1 - x0 = 0.06165 ns

Cell Fall Delay: The time taken for a 50% transition at the output(high to low) corresponding to a 50% transition at the input(low to high).
Using data points:
x0 = 4.078e-09, y0 = 1.65007
x1 = 4.05e-09, y1 = 1.65007
Cell fall delay = x1 - x0 = 0.028 ns

Fixing DRC errors in the Layout geometries:
Download the ‘drc_tests.tgz’ and move to the home directory
  wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

  Decompress the .tgz file
  $tar xfz drc_tests.tgz
  
Home directory route:
cd drc_tests/
ls -ltr

![image](https://github.com/user-attachments/assets/953caae7-0cf8-455e-aac5-a0eaf06c47fe)


Check and Open the .magicrc file in Vim
  gvim .magicrc
  $ magic -d XR &

In magic, File -> Open -> met3.mag

![image](https://github.com/user-attachments/assets/603b1db4-f3b7-4a32-9d35-45c9365e6e1e)



![image](https://github.com/user-attachments/assets/c114148d-b86e-4679-9f32-36807eda8089)


Clicking on 'Drc-->DRC Update' a few DRC violations will show. To examine them it is possible to click on 'DRC find next error' or to graphically enclose a cell with the cursor and entering the following command in tkcon:

drc why

![image](https://github.com/user-attachments/assets/13a1e2d1-995b-47a1-868e-c5f40a7686dc)


Open the poly.mag file to check for drc errors and fix them
In magic, File →Open → Poly.mag 


![image](https://github.com/user-attachments/assets/e5bf23b4-a4e5-46c4-9731-bf1e37ca8d9f)

Zoom the poly.9 using ‘S’ and create a box to identify the error and edit the sky130A.tech file 
accordingly


![image](https://github.com/user-attachments/assets/c7708cf3-c175-4a9d-83ca-d05ccfde531a)


Add ‘polynonres’ in poly.9 specific locations in the sky130A.tech file to fix the error


Load the updated tech file by typing the below command in tkcon window

tech load sky130A.tech

Run drc check to view the updated errors due to the update in the file

drc check
drc why


![image](https://github.com/user-attachments/assets/c08daa58-d309-4d5d-b719-1b01348e1e4f)


The difftap.2 rule is implemented wrong because there is no violation even though the spacing is 0.42u


![image](https://github.com/user-attachments/assets/0c9bef98-1d7d-4eac-89e3-010130cdb42c)

The periphery rule of poly.9 are mentioned below:


![image](https://github.com/user-attachments/assets/1b188d9f-b1ef-40a3-919f-6efd1f04ce67)



Open the nwell.4 file to check for drc errors and fix them
In magic, File →Open → nwell.4


![image](https://github.com/user-attachments/assets/1a629df5-ac73-4e67-8bb6-841e9dfaeab6)


Error: (nwell is untapped)


![image](https://github.com/user-attachments/assets/e9fab3cf-da48-4ba9-94b3-486c95e45e36)


Adding untapped nwell, subtracting other tapped nwell and setting all variants to 'full' in the sky130A.tech file:
 

![image](https://github.com/user-attachments/assets/748b4b9c-9588-435d-b3bf-17343d8f3e10)


The periphery rules for nwell.4 as mentioned by sky130PDK:

![image](https://github.com/user-attachments/assets/859da252-48e2-45fa-8154-82da9c2a8589)


Load the updated tech file by typing the below command in tkcon window

tech load sky130A.tech

Run drc check to view the updated errors due to the update in the file

drc check
drc why

Checking the nwell.9 file:


![image](https://github.com/user-attachments/assets/7294078f-4001-48de-9dbb-d399ce5b27ff)










































Day 4 : Pre-layout timing analysis and the importance of a good clock tree

Introduction to Delay Tables:
Delay tables play a critical role in timing analysis by providing a detailed representation of how signals propagate through various circuit components. These tables contain information about the delay characteristics of standard cells, interconnects, and macros, helping designers predict signal arrival times accurately.

Purpose of Delay Tables:
In modern VLSI design, achieving precise timing closure is crucial to ensure the circuit operates correctly at the desired clock frequency. Delay tables contribute to this by:
Modeling propagation delays through logic gates and interconnects.
Assisting timing analysis tools in evaluating signal transitions.
Enabling optimization of placement and routing based on real-time delay estimations.

During physical design, delay tables serve multiple functions:
Cell Characterization: Standard cells (such as NAND, NOR, and flip-flops) are characterized using delay tables based on factors like input transition time and output load capacitance.
Interconnect Modeling: Delays due to routing and parasitics are estimated using lookup tables derived from extracted parasitic data.
Static Timing Analysis (STA): Timing verification tools use delay tables to compute worst-case and best-case timing scenarios, ensuring that setup and hold requirements are met.

Types of Delay Representation:
Library Characterization Data (Lib Files) – These include lookup tables (LUTs) that provide delays based on input slew and output capacitance.
Parasitic Delay Models (SPEF, RSPF) – Account for wire delays and coupling effects.
Propagation Delay Tables – Define delays for individual gates under different operating conditions.


The objectives of the day are the following:
Integrate customised inverter cell design in OpenLANE flow
Timing analysis using ideal clocks with openSTA
Run Clock Tree Synthesis using TritonCTS
Timing analysis using real clocks with openSTA

Open the customised inverter cell layout in Magic with these commands:

  $ cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
  $ magic -T sky130A.tech sky130_inv.mag &


![image](https://github.com/user-attachments/assets/791d97a4-2781-400d-b9ce-457e38b9858e)


Open the tracks.info file of sky130_fd_sc_hd.


![image](https://github.com/user-attachments/assets/a16a4198-503a-4174-a7c9-6bfedbb98931)


Set grid values accordingly “grid 0.46um 0.34um 0.23um 0.17um” in the tkcon window


![image](https://github.com/user-attachments/assets/8e783c24-1770-4ee4-bd7d-d9b7521780c2)

Verify whether the following conditions are met:
1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
2: Width of the standard cell should be odd multiples of the horizontal track pitch.
3: Height of the standard cell should be even multiples of the vertical track pitch.

Save the inverter layout using this command in the tkcon window:
save sky130_inv.mag

To open the newly saved custom inverter layout, use:
magic -T sky130A.tech sky130_vsdinv.mag &


![image](https://github.com/user-attachments/assets/d57e0fb6-d282-408d-9495-d10e85a89e64)


Generate the lef file from the layout:(tkcon window)
lef write


![image](https://github.com/user-attachments/assets/3bae16c5-2481-43d1-8596-d5c42c286d5b)

Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
Commands to copy necessary files to 'picorv32a' design 'src' directory

Copy lef file: cp sky130_vsdinv.lef 

~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

Copy library files: cp libs/sky130_fd_sc_hd__* 

~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

Edit the config.tcl file 

![image](https://github.com/user-attachments/assets/40512a3f-4b0c-4556-a0b1-5348169dd096)


After this go to the openlane directory and run docker, followed by package version, design and run synthesis

prep -design picorv32a -tag 31-01_17-10 -overwrite


![image](https://github.com/user-attachments/assets/2c579639-74a1-48b0-a9d6-69c0c1ca3fdb)


Commands to include newly added lef to openlane flow:
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

Now run the synthesis:
Run_synthesis

Change parameters to improve timing and run synthesis
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) 1

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

Run the synthesis again to view the timing results again:
Run_synthesis


![image](https://github.com/user-attachments/assets/20e7fcba-0f70-44d4-9b26-82a0d5209af3)

 
Now run the floorplan 
 
run_floorplan

If the above command shows an error, use the following commands

Init_floorplan
Place_io
Tap_decap_or

![image](https://github.com/user-attachments/assets/580e6373-ee2a-46f1-8f01-63e4c19c8afd)


Now run the placement

run_placement

To view placement in Magic tool:
Change directory to path containing generated placement def: 
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17-10/results/placement/

Command to load the placement def in magic tool: 

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &


Timing analysis using ideal clocks with OpenSTA
Create two files:
pre_sta.conf
my_base.sdc


![image](https://github.com/user-attachments/assets/d73ba48a-6abb-4783-9b35-61177f742a2e)


Run the Static Timing analysis using the command below:

cd Desktop/work/tools/openlane_working_dir/openlane

sta pre_sta.conf

If there is any slack violations and tns,wns values are high, change the variable values again to reduce them

# prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Additional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

set ::env(SYNTH_STRATEGY) "DELAY 3"

echo $::env(SYNTH_BUFFERING)

echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

echo $::env(SYNTH_DRIVING_CELL)

echo $::env(SYNTH_MAX_FANOUT) 4

Run_synthesis


![image](https://github.com/user-attachments/assets/041a17a8-b7f1-4259-8a9f-3ec1a22db470)


Now the tns and wns value is minimized to 0.00.

Again running STA to reduce slack violations by manually reducing delays (if necessary)

Here we got the max delay as 0.81 (of '02560' net)


To reduce this delay we have to replace the cell under driver pins of desired net:


![image](https://github.com/user-attachments/assets/0f2e7bb7-bd4b-46d1-aa67-03d9b806aa4e)


Again running the STA and checking whether the maximum delay and slack is reduced:

As we can clearly see, the delay and slack is reduced by a significant factor.
To do basic timing ECO: report_checks -from _35312_ -to _35239_ -through _32503_

Now, replace some more cells to increase the ports and reduce the slack:


Initially the wns & slack violation was -36.62 and tns was -3854.15, but now wns & slack violation is -3.82(~89.5% reduction) and tns is -326.38(~91.5% reduction).
Now, overwrite this verilog file on the previous picorv32a verilog file that we got by synthesis: write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17-10/results/synthesis/picorv32a.synthesis.v

Exit from OpenSTA: 

exit 

Let's check whether our verilog file is being overwritten:

Post-CTS OpenROAD timing analysis
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/31-01_17-10/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/cts/picorv32a.cts.def

write_db pico_cts.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock \[all_clocks\]

help report_checks

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

Exit


![image](https://github.com/user-attachments/assets/78fe86ee-9c52-4a1c-8a0d-dc62d62433d0)



This will generate a hold and a setup report:
Screenshot of Hold report:


![image](https://github.com/user-attachments/assets/328deb1f-1f6b-4caf-9cff-2dbc4e1c37cb)


Screenshot of Hold report:


![image](https://github.com/user-attachments/assets/8bb92947-e25b-4bc3-9a4c-5f54e63d4c15)


Inboth the cases the timing slack is 'MET' and not violated.
But we can improve the slack even more, even though it has negative effect like increase in area. We can reduce the slack by removing the 'clkbuf_1' from the buffer list.

echo \$::env(CTS_CLK_BUFFER_LIST)

set ::env(CTS_CLK_BUFFER_LIST) \[lreplace \$::env(CTS_CLK_BUFFER_LIST) 0 0\]

echo \$::env(CTS_CLK_BUFFER_LIST)

echo \$::env(CURRENT_DEF)

set ::env(CURRENT_DEF)/openLANE_flow/designs/picorv32a/runs/17-01_14-04/results/placement/picorv32a.placement.def

run_cts

echo \$::env(CTS_CLK_BUFFER_LIST)
 

![image](https://github.com/user-attachments/assets/35aa40e2-104a-4bdf-bf9b-d491f401110e)



openroad

read_lef /openLANE_flow/designs/picorv32a/runs/31-01_17-10/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/cts/picorv32a.cts.def

write_db pico_cts.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/31-01_17-10/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock \[all_clocks\]

help report_checks

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

Exit

This will generate a hold and a setup report:
Screenshot of Hold report:


![image](https://github.com/user-attachments/assets/29317074-d233-4307-978a-fff583a86b43)


Screenshot of Hold report:


![image](https://github.com/user-attachments/assets/95b2079a-addd-46f7-bc3b-982390addc8f)


echo \$::env(CTS_CLK_BUFFER_LIST)

set ::env(CTS_CLK_BUFFER_LIST) \[linsert \$::env(CTS_CLK_BUFFER_LIST) 0
sky130_fd_sc_hd\_\_clkbuf_1\]

echo \$::env(CTS_CLK_BUFFER_LIST)

![image](https://github.com/user-attachments/assets/0d828d86-b52c-43c0-8980-995d70bfad71)

















DAY-5 Final steps for RTL2GDS using tritonRoute and openSTA 
The objectives of this section are 
Generation of the Power Distribution Network (PDN)
Detailed Routing using TritonRoute
Parasitic extraction
Post-routing timing analysis using OpenSTA

# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a -tag 31-01_17-10

# Check current def
echo  $::env(CURRENT_DEF)

# Now that CTS is done we can do power distribution network
gen_pdn


![image](https://github.com/user-attachments/assets/a877e7fe-6d3e-4b31-9266-ccdebc8141a9)


After running pdn, if we check CURRENT_DEF: echo $::env(CURRENT_DEF), it is now changed from 'picorv32a.cts.def' to '17-pdn.def'

![image](https://github.com/user-attachments/assets/661886e4-685c-4f9b-9626-abf85dd6b704)



Now run routing: run_routing i.e., zero violations while running the routing process.


![image](https://github.com/user-attachments/assets/925137c6-d058-4375-bd06-9b338f9c860f)


Now to load the PDN DEF in Magic:
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-01_17_10/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 17-pdn.def &



Screenshots of final PDN layout in Magic:


![image](https://github.com/user-attachments/assets/5fe7d834-1b76-4cba-9fa5-cd95f9c01d2d)


Zoomed_in:

Exploring the Layout and getting idea of design: 


![image](https://github.com/user-attachments/assets/7c0bd02f-6837-4380-b2c0-cacd09b4e4af)



PDN def image:


![image](https://github.com/user-attachments/assets/70233648-3764-418e-966f-eba8a6a0e7e4)

The final step is Post-routing setup and hold STA report


Acknowledgements
Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd.
Nickson P Jose, Physical Design Engineer, Intel Corporation.
R. Timothy Edwards, Senior Vice President of Analog and Design, efabless Corporation.











