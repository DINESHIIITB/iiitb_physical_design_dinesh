# iiitb_physical_design_dinesh


[week 0](#week_0)

[Day 1](#day-1)

[Day 2](#day-2)

[Day 3](#day-3)

[Day 4](#day-4)

[Day 5](#day-5)


# week_0

## Day 1

<details>
 <summary> Installing the necessary tools </summary>


### **OpenSTA**

 I installed and built OpenSTA (including the needed packages) using the following commands:
 ```
sudo apt-get install cmake clang gcctcl swig bison flex
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
```
Below is the screenshot showing sucessful installation:
![image](https://github.com/DINESHIIITB/Dinesh_iiitb_asic/assets/140998565/7ca9dc6e-e1b7-4d38-bcd9-60796a902546)


### **Openlane**

Prior to the installation of the OpenLane install the dependencies and packages using the command shown below :</br>
``` 
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation :</br>
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 


# Check for installation
sudo docker run hello-world
```

**Steps to install OpenLane, PDKs and Tools**</br>
```
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```
</details>


<details>
 <summary> Reduced Instruction Set Computer (RISC) </summary>


### Reduced Instruction Set Computer (RISC)

RISC-V is an open-source instruction set architecture (ISA).An instruction set architecture defines the set of instructions a processor can execute. RISC-V offers multiple base instruction sets (RV32I, RV64I, etc.) and optional standard extensions (e.g., M for integer multiplication/division, F for single-precision floating-point, D for double-precision floating-point, and more). This modularity allows designers to tailor the architecture to their specific needs.

Compilation: Use a C compiler (e.g., GCC, Clang) to compile the C source code into assembly code. The compiler translates the high-level C code into low-level assembly code that the hardware can understand.

Assembly: Assemble the generated assembly code using an assembler (e.g., GNU Assembler - GAS). The assembler converts the assembly code into machine code, which consists of binary instructions that the hardware can directly execute. The type of instructions depend on what type of hardware it is, if it is risc v then the instructions are also risc v.

Loading: Load the generated executable binary onto the target hardware. This can involve transferring the binary to a microcontroller, FPGA, or other hardware platform via appropriate interfaces (e.g., JTAG, USB, SD card).

Execution on Hardware: Run the program on the target hardware. The hardware's CPU fetches and executes the machine code instructions, carrying out the logic specified in the C source code.


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/f3d963b3-c93e-4e94-9d33-a852e837ab47)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/c08f0252-fc86-4b41-868f-327212a3da2b)

</details>

<details>
 <summary> ASIC Design </summary>

### ASIC Designs

For ASIC design we require 

 1. EDA Tools : EDA tools are essential for ASIC design. These tools assist in various stages of the design process, including RTL design, simulation, synthesis, physical design, and verification. Some commonly used EDA tools include:
    * RTL Design Tools: Such as Cadence Encounter, Synopsys Design Compiler, or Xilinx Vivado for writing and simulating RTL code.
    * Simulation Tools: Tools like Cadence SimVision, Synopsys VCS, or ModelSim for simulating the ASIC's behavior before fabrication.
    * Synthesis Tools: Used to convert RTL code into gate-level netlists. Synopsys DC (Design Compiler) and Cadence Genus are examples.
    * Physical Design Tools: This includes Cadence Innovus, Synopsys IC Compiler, or Mentor Graphics Calibre for physical layout and optimization.
    * Verification Tools: Tools like Cadence Incisive, Synopsys VCS, or formal verification tools like Cadence JasperGold are used for verifying the design's correctness.
   
      * OPen EDA tools:
        1. QFLow
        2. OPenroad
        3. OPenlane

 2. Process Design Kits (PDKs): PDKs are essential sets of files and data provided by semiconductor foundries. They contain information about the manufacturing process, including transistor models, design rules, and technology files. ASIC designers use PDKs to ensure their designs are compatible with the foundry's manufacturing process.
      * SKY water 130nm PDK
      * ![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9eff7965-168b-43d3-83ef-84a7f6d20f2a)

 3. RTL (Register-Transfer Level) Design: RTL design is a critical aspect of ASIC design. You'll need to write RTL code using hardware description languages (HDLs) like VHDL or Verilog.
    * Sorces for RTL Design:
       * Librecores.org
       * OPencores.org
       * githhub


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/6312baa3-4225-4c02-810d-af8f313de0f0)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/d56920d8-aa12-4a39-b85c-fb2677f563f3)

</details>

<details>
 <summary> RTL to GDS </summary>


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9c724efe-34a6-4e24-b818-8297a0e4eb3e)

1. Synthesis: The RTL code is synthesized to generate a gate-level netlist using synthesis tools such as Cadence Genus, Synopsys Design Compiler, or similar tools. The gate-level netlist represents the design using logical gates, flip-flops, and other standard cells.

2. Floorplanning: Create a physical floorplan for your design, which defines the placement of different modules and cells on the silicon die. Proper floorplanning can significantly impact the ASIC's performance, power consumption, and manufacturability.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b69b48da-4b80-451a-8b2d-d7470b522de1)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/a8ff07b6-b657-4a88-b650-ac83654c7255)

3. Placement: Based on the floorplan, use a place-and-route tool (e.g., Cadence Innovus, Synopsys ICC) to place the standard cells and modules on the chip's layout. This step also involves optimizing the placement for factors like power and signal integrity.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e2bed2d2-389c-4e23-b45e-983fab17b5c4)

4. Clock Tree Synthesis (CTS): Design and implement the clock distribution network to ensure proper clocking of the ASIC. Clock tree synthesis tools like Cadence Innovus or Synopsys IC Compiler can be used for this purpose.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/29d3e2f4-e1bd-4cf6-851a-dec4f5c7fb9a)

5. Routing: After placement, the routing phase involves connecting the placed cells and modules with metal traces to establish the desired interconnections. The routing tool generates the detailed layout of the chip.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/08145132-edf3-4b41-a3a1-54c98ab2bf44)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/85e26eab-e126-4d17-aeed-17ed65cbe596)


6. Signoff:
   * Physical Verification: Perform various physical verification checks to ensure that the layout adheres to the design rules and manufacturing constraints. These checks include DRC (Design Rule Checking) and LVS (Layout vs. Schematic) checks.
   * Extraction: Extract parasitic information from the layout, which is used in subsequent steps for more accurate timing analysis.
   * Final Timing Closure: Re-run static timing analysis (STA) to ensure that the design still meets the required timing constraints, considering the parasitics from the extraction step. Iterate on placement and routing if necessary.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/54272ca3-7de1-4a92-9310-10730a8dd5c9)


</details>


<details>
 <summary> Openlane tools </summary>

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/2f510c9b-197d-47da-bf38-2165e34622e5)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/2ececf08-92b5-4c09-8fa7-97a80f4f4c97)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/1f05a13d-c3cb-490a-9129-b14779933fbc)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/bc21f175-2dc9-4e53-be3e-9598fd27c7f3)



![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/399fb969-d135-4a94-b443-dd6bfe8ee563)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/7dbff85b-b474-4933-a47e-f5bb179210c4)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/1dfd2c20-95fc-4494-881a-53fb554639e2)

Labwork

ls -ltr ---> lists in chronological order
./flow.tcl ---> command says how the flow has to go

```
cd openlane
make mount
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
```

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/f14f6292-ba06-4468-b4cb-74236299b737)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/7ee2709c-38dd-4c57-9f82-0820fdf43a91)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/339464d8-cec4-48a0-82e5-75ca305b265b)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/36ed8cb9-002d-4937-b85a-11fdcc20b63a)

</details>


## Day 2

### Good floorplan Bad floorplan and Introduction to library cells 

<details>
 <summary> Chip floor planning considerations </summary>

Netlist : A Netlist describes the connectivity of elcetronic design

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9e132084-0c38-47fc-a208-6490c53bbf6a)

Core : A Core is the section of the chip where the fundamental logic of the design is placed

Die : A Die which consists  core is small specimen material specimen on which the fundamentals circuit is fabricated.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b80fc877-078e-4bc4-8439-ec0dcaf5a686)

 ```                       
 Utilization factor =    ( Area occupied by netlist)/ (Total area of the core)
                                           
 Aspect ratio =  Height/Width
```
                                          
![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/0d22263a-e2e5-4131-a447-3a6e6582c913)

THe combinational logic can be divideed into two blocks with inputs and outputs and these blocks can be reused seperately or opgether whenver we want

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b84ee19c-f57a-4835-81c6-056417c59392)

3. Pre placed cells :   Preplaced cells in integrated circuit (IC) design are static, preconfigured logic or functional units that are strategically positioned within the IC layout. Design engineers manually place these cells at precise locations on the chip's layout canvas. Importantly, these preplaced cells retain their fixed positions throughout subsequent stages of the IC design process, including placement and routing. Typically, these cells house intricate logic or specialized functional blocks that are essential to the chip's overall functionality. Examples of preplaced cells encompass memory modules, customized processors, analog circuitry, specialized accelerators, or licensed Intellectual Property (IP) components.
   
![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/65afe218-3477-4994-9179-241ef37f9654)


Because of large distance between power and circuit the volatge at the circuit may enter undefind regions so to solve these problem we added decoupling capacitor parrallel to the circuit  to charge the circuit.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/624a8570-03ac-48d6-9b68-4b3a4594584b)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/818e86a1-d8e2-44dc-96ee-412fd0e515a9)

4.) Power Planning :

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/1da93907-ba9f-4b5d-bdf6-5619815c97bc)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/955e3157-711c-451d-8bdc-f88ec866aad6)

Power has supplied from multiple points to solve this problem.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e5d45acc-6b27-4568-8716-0d916d18eeff)

5.) Pin Placement : Pin placement, also referred to as I/O (Input/Output) planning or pin assignment, stands as a pivotal facet of integrated circuit (IC) design. It encompasses the meticulous determination of where and how to assign pins or external connections on the chip package. The significance of precise pin placement resonates across functionality, manufacturability, and overall performance. Through judicious pin arrangement, the integrity of signals can be maintained, averting signal degradation and ensuring the accuracy of data transmission. Prudent pin placement can also play a role in managing thermal aspects within the device. By strategically positioning power and ground pins, effective heat dissipation can be achieved. A well-considered approach to pin placement contributes to the reliability of the electronic system, diminishing the risks associated with signal issues, overheating, and manufacturing discrepancies.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b72a824e-86dd-4c0b-bd83-67cdf9e0c746)

run_floorplan

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b031b72f-66df-4df9-afce-49374b0be1be)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/17626251-9e92-4d1f-a5f7-96af025e5f60)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/8285c7d2-ca7c-4cb9-a2c0-1f6caa2b980d)

</details>



<details>
 <summary> Library binding and placement </summary>


Library contains following information:
1. Width and height of cells
2. the required conditon of particular cell
3. Delay information of cells
4. various sizes of same cells
 ![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b5c997d7-386f-4581-9aa7-0f2cf2dca2b0)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/48e22baa-d19f-4506-9fa2-299804fe587b)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/3e7d6d15-b14a-4104-a6ed-9e51d0adb308)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/f8d8a911-7c98-49b7-9c71-51f524bbf893)


</details>



<details>
 <summary> Cell design and characterization follows </summary>

Introduction

In the realm of digital integrated circuit design, standard cells play a pivotal role. These standard cells are pre-designed and pre-characterized building blocks, encompassing logic gates, flip-flops, latches, and various digital components, readily available in libraries. This documentation outlines the key aspects of the Standard Cell Design and Characterization process.

Standard Cell Design Flow

The process of standard cell design unfolds as follows:

1. Inputs:
   * Process Design Kits (PDKs): Essential for understanding the fabrication process.
   * Design Rule Check (DRC) & Layout vs. Schematic (LVS) Rules: Ensure design compliance with manufacturing rules.
   * SPICE Models: Utilized for simulation and analysis.
   * Libraries: Containing standard cell definitions.
   * User-Defined Specifications: Tailoring the design to meet specific requirements.

2. Design Steps:
   * Circuit Design: Defining the logical behavior of the standard cell.
   * Layout Design: Crafted using techniques like Euler's path and stick diagrams.
   * Extraction of Parasitics: Identifying and quantifying parasitic elements.
   * Characterization: Assessing timing, noise, and power characteristics.

3. Outputs:
   * Circuit Description Language (CDL): A textual representation of the cell.
   * Layout Exchange Format (LEF): A format for sharing layout information.
   * GDSII: A standard file format for mask data.
   * Extracted SPICE Netlist (.cir): A file detailing the electrical components.
   * Timing, Noise, and Power .lib Files: Libraries with critical data for circuit optimization.

Standard Cell Characterization Flow

Characterization is the process of comprehensively evaluating electrical and performance characteristics of specific standard cells or library elements. It is crucial for understanding cell behavior under various operational conditions. The characterization process unfolds as follows:

1. Read in the Models and Tech Files: Gathering essential data and technology specifications.
2. Read Extracted SPICE Netlist: Accessing the electrical representation of the cell.
3. Recognize Behavior of the Cell: Understanding the cell's functionality.
4. Read the Subcircuits: Analyzing component subcircuits within the cell.
5. Attach Power Sources: Connecting power supplies to simulate real-world conditions.
6. Apply Stimulus to Characterization Setup: Providing input signals for testing.
7. Provide Necessary Output Capacitance Loads: Mimicking the load conditions.
8. Provide Necessary Simulation Commands: Configuring simulation settings.

For standard cell characterization, we recommend utilizing the open-source software, GUNA. This software streamlines the process by taking input from steps 1 to 8 and generates critical timing, noise, and power models. These models are indispensable for the precise design and optimization of digital circuits using standard cells.



</details>



<details>
 <summary> General timing characterization parameters </summary>

 #### Timing threshold Definitions

  1. slew_low_rise_thr: This is the threshold at which the rising signal (transition from low to high) reaches 20% of its full value.
  2. slew_high_rise_thr: This is the threshold at which the rising signal reaches 80% of its full value.
  3. slew_low_fall_thr: This is the threshold at which the falling signal (transition from high to low) reaches 20% of its full value.
  4. slew_high_fall_thr: This is the threshold at which the falling signal reaches 80% of its full value.
  5. in_rise_thr: This is the threshold for the input signal during its rising transition, typically set at 50% of its full value.
  6. in_fall_thr: This is the threshold for the input signal during its falling transition, also set at 50% of its full value.
  7. out_rise_thr: This is the threshold for the output signal during its rising transition, again set at 50% of its full value.
  8. out_fall_thr: This is the threshold for the output signal during its falling transition, also set at 50% of its full value.

* Propagation Delay:

Propagation delay is the time it takes for a change in an input signal to propagate through a digital circuit and reach 50% of its final value in the output signal. It is a critical parameter for assessing circuit performance and signal timing.

Mathematically, propagation delay can be expressed as:

 Propagation Delay = time(out_fall_thr) - time(in_rise_thr)
          * time(out_fall_thr) is the time when the output signal reaches 50% of its final value during its falling transition.
          *  time(in_rise_thr) is the time when the input signal reaches 50% of its final value during its rising transition.

* Transition Time:

Transition time refers to the duration it takes for a digital signal to change its voltage level from one logic state (e.g., logic low or 0) to another logic state (e.g., logic high or 1), or vice versa. Transition time is essential for assessing how quickly a signal can switch between logic states.

There are two types of transition times:

1. Fall Transition Time:
    Fall transition time measures the duration it takes for a signal to transition from a high voltage level to a low voltage level. It can be calculated as:
Fall Transition Time = time(slew_high_fall_thr) - time(slew_low_fall_thr)

     * time(slew_high_fall_thr) is the time when the falling signal reaches 80% of its final value.
     * time(slew_low_fall_thr) is the time when the falling signal reaches 20% of its final value.

2. Rise Transition Time:
Rise transition time measures the duration it takes for a signal to transition from a low voltage level to a high voltage level. It can be calculated as:

Rise Transition Time = time(slew_high_rise_thr) - time(slew_low_rise_thr)

    * time(slew_high_rise_thr) is the time when the rising signal reaches 80% of its final value.
    * time(slew_low_rise_thr) is the time when the rising signal reaches 20% of its final value.

</details>

### Day 3

### Design library cell using magic layout and ngspice characterization 

<details>
 <summary> CMOS inverter ngspice simulations </summary>


In this section, we will outline the process of creating a SPICE deck and conducting simulations for a CMOS inverter using NGSpice. The CMOS inverter consists of complementary metal-oxide-semiconductor (CMOS) components, including both p-type (PMOS) and n-type (NMOS) transistors.

### SPICE Deck Creation and Simulation for CMOS Inverter:

    SPICE Deck: A SPICE deck refers to the component connectivity, essentially a netlist, for the CMOS inverter. It defines how components are connected within the circuit.

    SPICE Deck Values: Specify the values for key parameters, such as W/L (Width/Length). For example, "0.375u/0.25u" indicates that the width is 375 nanometers, and the length is 250 nanometers. It's essential to note that PMOS transistors should have a wider width compared to NMOS transistors, often 2x or 3x wider. Gate and supply voltages are typically multiples of the length; for instance, the gate voltage might be set at 2.5 volts.

    Add Nodes: Surround each component in your circuit with nodes and assign unique names to these nodes. These node names are used in the SPICE netlist to identify and connect components properly.

Additional Notes:

    Width vs. Length: In CMOS technology, "width" refers to the length of the source and drain regions, while "length" denotes the distance between the source and drain. These parameters significantly impact the performance of transistors.

    PMOS and NMOS Sizing: PMOS transistors typically have slower carrier mobility (holes) compared to NMOS transistors (electrons). To achieve balanced rise and fall times in your CMOS inverter, the PMOS transistor should have a larger width, reducing its resistance and increasing mobility.

   * SPICE Deck netlsit description
     
 ![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/87fad89f-75dc-4c0e-a44d-696ac694855e)

***syntax for PMOS and NMOS desription***
[component name] [drain] [gate] [source] [substrate] [transistor type] W=[width] L=[length]

 ***simulation commands***
.op --- is the start of SPICE simulation operation where Vin will be sweep from 0 to 2.5 with 0.5 steps
tsmc_025um_model.mod  ----  model file containing the technological parameters for the 0.25um NMOS and PMOS 

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/4c5384a4-f831-48fd-b4f4-8768f696e35f)

 Determining CMOS Switching Threshold Vm

The switching threshold, denoted as Vm, in CMOS circuits is a critical parameter that depends on several factors. It represents the input voltage (Vin) at which the output voltage (Vout) switches, signifying that both the PMOS and NMOS transistors are in saturation or turned on, leading to higher leakage current. Here are the key factors influencing the robustness of CMOS switching threshold Vm:

    Transistor Sizing: The relative sizes (width/length ratios, W/L) of PMOS and NMOS transistors play a significant role. If the PMOS transistor is larger (thicker) than the NMOS transistor, the CMOS circuit tends to have a higher switching threshold (e.g., 1.2V). Conversely, when the NMOS transistor is larger, the threshold voltage tends to be lower (e.g., 1V). This size relationship affects the balance of carrier mobility and resistance in the transistors.

    Saturation Region: The switching threshold occurs when both the PMOS and NMOS transistors are in the saturation region. In this state, both transistors are turned on, and there is a high likelihood of current flowing directly from the supply voltage (VDD) to ground (GND). This is often referred to as leakage current, and minimizing it is essential for power efficiency.

To find the switching threshold Vm during DC transfer analysis, the following SPICE simulation commands are used with a DC input of 2.5V, sweeping the input voltage from 0V to 2.5V in 0.05V steps:

plaintext

Vin in 0 2.5
*** Simulation Command ***
.op
.dc Vin 0 2.5 0.05


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/4ba84476-cc3a-4d0d-b322-c7ecb3f2988d)

#### Labs


Each cell that is placed on the layout is referred to as standard cell. Standard cells are pre-designed and pre-characterized logic gates, flip-flops, latches, and other digital components for which the definition is available in libraries.

Standard Cell Design Flow

Standard cell design flow involves the following:
* Inputs: PDKs, DRC & LVS rules, SPICE models, libraries, user-defined specifications
* Design steps: Circuit design, Layout design (Art of layout Euler's path and stick diagram), Extraction of parasitics, Characterization (timing, noise, power)
* Outputs: CDL (circuit description language), LEF, GDSII, extracted SPICE netlist (.cir), timing, noise and power .lib files

Standard Cell Characterization Flow

Characterization refers to the process of gathering and analyzing electrical and performance data for a specific cell or library element. The goal of characterization is to provide accurate and comprehensive information about how the cell behaves under various operating conditions. This information is essential for designing and optimizing digital circuits using these cells.

A typical standard cell characterization flow includes the following steps:
1. Read in the models and tech files
2. Read extracted spice netlist
3. Recognise behaviour of the cell
4. Read the subcircuits
5. Attach power sources
6. Apply stimulus to characterization setup
7. Provide necessary output capacitance loads
    Provide necessary simulation commands the opensource software called GUNA can be used for characterization. Steps 1-8 are fed into the GUNA software which generates timing, noise and power models.
   
#### Standard Cell Design Flow
      Inputs:
            * Process Design Kits (PDKs
            * Design Rule Check (DRC) & Layout vs. Schematic (LVS) rules.
            * SPICE models
            Libraries
            User-defined specifications
        Design Steps:
            Circuit design
            Layout design (Art of layout Euler's path and stick diagram)
            Extraction of parasitics
            Characterization (timing, noise, power)
        Outputs:
            Circuit Description Language (CDL)
            Layout Exchange Format (LEF)
            GDSII layout files
            Extracted SPICE netlist (.cir)
            Timing, noise, and power .lib files

    Standard Cell Characterization Flow
        Characterization Steps:
            Read in the models and tech files
            Read the extracted SPICE netlist
            Recognize the behavior of the cell
            Read the subcircuits
            Attach power sources
            Apply stimulus to the characterization setup
            Provide necessary output capacitance loads
            Provide necessary simulation commands
        Characterization Tool:
            The open-source software GUNA is recommended for characterization.
        Output:
            GUNA software generates timing, noise, and power models.


Each cell that is placed on the layout is referred to as standard cell. Standard cells are pre-designed and pre-characterized logic gates, flip-flops, latches, and other digital components for which the definition is available in libraries.

Standard Cell Design Flow

Standard cell design flow involves the following:

    Inputs: PDKs, DRC & LVS rules, SPICE models, libraries, user-defined specifications
    Design steps: Circuit design, Layout design (Art of layout Euler's path and stick diagram), Extraction of parasitics, Characterization (timing, noise, power)
    Outputs: CDL (circuit description language), LEF, GDSII, extracted SPICE netlist (.cir), timing, noise and power .lib files

Standard Cell Characterization Flow

Characterization refers to the process of gathering and analyzing electrical and performance data for a specific cell or library element. The goal of characterization is to provide accurate and comprehensive information about how the cell behaves under various operating conditions. This information is essential for designing and optimizing digital circuits using these cells.

A typical standard cell characterization flow includes the following steps:
1. Read in the models and tech files
2. Read extracted spice netlist
3. Recognise behaviour of the cell
4. Read the subcircuits
5. Attach power sources
6. Apply stimulus to characterization setup
7. Provide necessary output capacitance loads
     Provide necessary simulation commands the opensource software called GUNA can be used for characterization. Steps 1-8 are fed into the GUNA software which generates timing, noise and power models.

Standard Cell Design and Characterization

Introduction

In the realm of digital integrated circuit design, standard cells play a pivotal role. These standard cells are pre-designed and pre-characterized building blocks, encompassing logic gates, flip-flops, latches, and various digital components, readily available in libraries. This documentation outlines the key aspects of the Standard Cell Design and Characterization process.

Standard Cell Design Flow

The process of standard cell design unfolds as follows:

Inputs:
    * Process Design Kits (PDKs): Essential for understanding the fabrication process.
    * Design Rule Check (DRC) & Layout vs. Schematic (LVS) Rules: Ensure design compliance with manufacturing rules.
    SPICE Models: Utilized for simulation and analysis.
    Libraries: Containing standard cell definitions.
    User-Defined Specifications: Tailoring the design to meet specific requirements.

Design Steps:

    Circuit Design: Defining the logical behavior of the standard cell.
    Layout Design: Crafted using techniques like Euler's path and stick diagrams.
    Extraction of Parasitics: Identifying and quantifying parasitic elements.
    Characterization: Assessing timing, noise, and power characteristics.

Outputs:

    Circuit Description Language (CDL): A textual representation of the cell.
    Layout Exchange Format (LEF): A format for sharing layout information.
    GDSII: A standard file format for mask data.
    Extracted SPICE Netlist (.cir): A file detailing the electrical components.
    Timing, Noise, and Power .lib Files: Libraries with critical data for circuit optimization.

Standard Cell Characterization Flow

Characterization is the process of comprehensively evaluating electrical and performance characteristics of specific standard cells or library elements. It is crucial for understanding cell behavior under various operational conditions. The characterization process unfolds as follows:

    Read in the Models and Tech Files: Gathering essential data and technology specifications.
    Read Extracted SPICE Netlist: Accessing the electrical representation of the cell.
    Recognize Behavior of the Cell: Understanding the cell's functionality.
    Read the Subcircuits: Analyzing component subcircuits within the cell.
    Attach Power Sources: Connecting power supplies to simulate real-world conditions.
    Apply Stimulus to Characterization Setup: Providing input signals for testing.
    Provide Necessary Output Capacitance Loads: Mimicking the load conditions.
    Provide Necessary Simulation Commands: Configuring simulation settings.

For standard cell characterization, we recommend utilizing the open-source software, GUNA. This software streamlines the process by taking input from steps 1 to 8 and generates critical timing, noise, and power models. These models are indispensable for the precise design and optimization of digital circuits using standard cells.



1. slew_low_rise_thr: This is the threshold at which the rising signal (transition from low to high) reaches 20% of its full value.
2. slew_high_rise_thr: This is the threshold at which the rising signal reaches 80% of its full value.
3. slew_low_fall_thr: This is the threshold at which the falling signal (transition from high to low) reaches 20% of its full value.
4. slew_high_fall_thr: This is the threshold at which the falling signal reaches 80% of its full value.
5. in_rise_thr: This is the threshold for the input signal during its rising transition, typically set at 50% of its full value.
6. in_fall_thr: This is the threshold for the input signal during its falling transition, also set at 50% of its full value.
7. out_rise_thr: This is the threshold for the output signal during its rising transition, again set at 50% of its full value.
8. out_fall_thr: This is the threshold for the output signal during its falling transition, also set at 50% of its full value.

These thresholds are crucial for timing analysis in digital circuits. They help determine when signals have transitioned to specific voltage levels, which is essential for proper circuit operation and signal integrity.


Propagation Delay:
Propagation delay is the time it takes for a change in an input signal to propagate through a digital circuit and reach 50% of its final value in the output signal. It is a critical parameter for assessing circuit performance and signal timing.

Mathematically, propagation delay can be expressed as:

Propagation Delay = time(out_fall_thr) - time(in_rise_thr)

* time(out_fall_thr) is the time when the output signal reaches 50% of its final value during its falling transition.
* time(in_rise_thr) is the time when the input signal reaches 50% of its final value during its rising transition.

Transition Time:
Transition time refers to the duration it takes for a digital signal to change its voltage level from one logic state (e.g., logic low or 0) to another logic state (e.g., logic high or 1), or vice versa. Transition time is essential for assessing how quickly a signal can switch between logic states.

There are two types of transition times:

1. Fall Transition Time:
Fall transition time measures the duration it takes for a signal to transition from a high voltage level to a low voltage level. It can be calculated as:

Fall Transition Time = time(slew_high_fall_thr) - time(slew_low_fall_thr)

* time(slew_high_fall_thr) is the time when the falling signal reaches 80% of its final value.
* time(slew_low_fall_thr) is the time when the falling signal reaches 20% of its final value.

2. Rise Transition Time:
Rise transition time measures the duration it takes for a signal to transition from a low voltage level to a high voltage level. It can be calculated as:


    Rise Transition Time = time(slew_high_rise_thr) - time(slew_low_rise_thr)

* time(slew_high_rise_thr) is the time when the rising signal reaches 80% of its final value.
* time(slew_low_rise_thr) is the time when the rising signal reaches 20% of its final value.

These parameters are vital for assessing the speed and performance of digital circuits and are critical in ensuring that signals switch reliably and within specified timing constraints.

CMOS inverter ngspice simulations

SPICE Deck creation and simulation for CMOS Inverter:

    SPICE deck = component connectivity (basically a netlist) of the CMOS inverter.
    SPICE deck values = value for W/L (0.375u/0.25u means width is 375nm and lengthis 250nm). PMOS should be wider in width(2x or 3x) than NMOS. The gate and supply voltages are normally a multiple of length (in the example, gate voltage can be 2.5V)
    Add nodes to surround each component and name it. This will be used in SPICE to identify a component.

Notes:

    Width is the length of source and drain. Length is the distance between source and drain.
    PMOS hole carrier is slower than NMOS electron carrier mobility, so to match the rise and fall time PMOS must be thicker (less resistance thus higher mobility) than NMOS.


CMOS Inverter NGSpice Simulations

In this section, we will outline the process of creating a SPICE deck and conducting simulations for a CMOS inverter using NGSpice. The CMOS inverter consists of complementary metal-oxide-semiconductor (CMOS) components, including both p-type (PMOS) and n-type (NMOS) transistors.

SPICE Deck Creation and Simulation for CMOS Inverter:

    SPICE Deck: A SPICE deck refers to the component connectivity, essentially a netlist, for the CMOS inverter. It defines how components are connected within the circuit.

    SPICE Deck Values: Specify the values for key parameters, such as W/L (Width/Length). For example, "0.375u/0.25u" indicates that the width is 375 nanometers, and the length is 250 nanometers. It's essential to note that PMOS transistors should have a wider width compared to NMOS transistors, often 2x or 3x wider. Gate and supply voltages are typically multiples of the length; for instance, the gate voltage might be set at 2.5 volts.

    Add Nodes: Surround each component in your circuit with nodes and assign unique names to these nodes. These node names are used in the SPICE netlist to identify and connect components properly.

Additional Notes:

    Width vs. Length: In CMOS technology, "width" refers to the length of the source and drain regions, while "length" denotes the distance between the source and drain. These parameters significantly impact the performance of transistors.

    PMOS and NMOS Sizing: PMOS transistors typically have slower carrier mobility (holes) compared to NMOS transistors (electrons). To achieve balanced rise and fall times in your CMOS inverter, the PMOS transistor should have a larger width, reducing its resistance and increasing mobility.

This approach ensures proper operation and desired characteristics for your CMOS inverter circuit during NGSpice simulations.
User
Switching Threshold Vm CMOS robustness depends on:

    Switching threshold = Vin is equal to Vout. This the point where both PMOS and NMOS is in saturation or kind of turned on, and leakage current is high. If PMOS is thicker than NMOS, the CMOS will have higher switching threshold (1.2V vs 1V) while threshold will be lower when NMOS becomes thicker.
    At this point, both the transistors are in saturation region, means both are turned on and have high chances of current flowing driectly from VDD to Ground called Leakage current.

DC transfer analysis is used for finding switching threshold. SPICE DC analysis below uses DC input of 2.5V. Simulation operation is DC sweep from 0V to 2.5V by 0.05V steps:

Vin in 0 2.5
*** Simulation Command ***
.op
.dc Vin 0 2.5 0.05


Determining CMOS Switching Threshold Vm

The switching threshold, denoted as Vm, in CMOS circuits is a critical parameter that depends on several factors. It represents the input voltage (Vin) at which the output voltage (Vout) switches, signifying that both the PMOS and NMOS transistors are in saturation or turned on, leading to higher leakage current. Here are the key factors influencing the robustness of CMOS switching threshold Vm:

    Transistor Sizing: The relative sizes (width/length ratios, W/L) of PMOS and NMOS transistors play a significant role. If the PMOS transistor is larger (thicker) than the NMOS transistor, the CMOS circuit tends to have a higher switching threshold (e.g., 1.2V). Conversely, when the NMOS transistor is larger, the threshold voltage tends to be lower (e.g., 1V). This size relationship affects the balance of carrier mobility and resistance in the transistors.

    Saturation Region: The switching threshold occurs when both the PMOS and NMOS transistors are in the saturation region. In this state, both transistors are turned on, and there is a high likelihood of current flowing directly from the supply voltage (VDD) to ground (GND). This is often referred to as leakage current, and minimizing it is essential for power efficiency.

To find the switching threshold Vm during DC transfer analysis, the following SPICE simulation commands are used with a DC input of 2.5V, sweeping the input voltage from 0V to 2.5V in 0.05V steps:

plaintext

Vin in 0 2.5
*** Simulation Command ***
.op
.dc Vin 0 2.5 0.05

This simulation process helps determine the precise voltage point at which the CMOS circuit transitions from one logic state to another, facilitating robust and efficient digital circuit design.
User

Clone Required Files:

 First, clone the required mag files and spicemodels of inverter,pmos and nmos sky130. 
 The command to clone files from github link is:
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

once I run this command, it will create vsdstdcelldesign folder in openlane directory.

Inorder to open the mag file and run magic go to the directory

For layout we run magic command

magic -T sky130A.tech sky130_inv.mag &

Cloning and Running Magic for Sky130 Inverter Layout

To work with the Sky130 inverter layout using the Magic tool, follow these steps:

Clone Required Files:
First, clone the required Mag (Magic layout files) and Spice Models for the inverter, PMOS, and NMOS from the GitHub repository using the following command:


git clone https://github.com/nickson-jose/vsdstdcelldesign.git

This command will create a vsdstdcelldesign folder within your openlane directory.

Open Magic Tool:
Navigate to the directory where the layout files are located. In your case, it's likely within the vsdstdcelldesign folder. To open the Magic tool, run the following command:

bash

magic -T sky130A.tech sky130_inv.mag &

    -T sky130A.tech specifies the technology file, which defines the parameters and rules for the Sky130 process.
    sky130_inv.mag is the layout file for the inverter.

The ampersand (&) at the end of the command allows you to keep the command line free for further use while Magic runs in the background.

Inspect Layout:
After running the above command, the Magic window should open, displaying the layout of the inverter. You can use Magic's features to inspect, modify, and analyze the layout as needed.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/05fd9056-5879-4643-ae8e-2104f5b15f20)



</details>

<details>
 <summary> Inception of Layout and CMOS Fabrication Process </summary>

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/ec6dada8-066b-4c6a-b1fe-54d22897477c)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/12308d20-c673-42a8-a7bc-4109dc8b6d03)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b37370bd-a004-4652-9f80-89584e96500a)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/77a6edaf-2b64-4f6d-bf91-7e6a71597f98)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/818989ba-25db-474a-9f53-bd1c41d278d5)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/53fc6fbd-7181-482c-af97-803495206834)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/1d5360a0-6760-4ba7-a420-093cb31c1868)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/599c4af1-2ff7-429c-a188-39daba1c8ed7)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/2355141d-b05c-4423-a536-0f4336455d1e)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e5ce8212-1bbe-4bc0-9c19-a4bfbff56779)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/7e016e74-8870-4c4b-b60c-6f3de44aecca)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/6aabcdda-8e21-4d6d-84a6-788caef6c1cb)


</details>

### Day 4

<details>
 <summary> Timing Analysis and Clock Tree Synthesis (CTS)  </summary>

#### Standard Cell LEF generation

To create a custom standard cell, you should adhere to the following guidelines:
1. Ensure that the input and output ports are positioned at the intersection of horizontal and vertical tracks.
2. Make sure that the width and height of the standard cell are both odd multiples of the horizontal track pitch and vertical track pitch.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e25b1545-0113-4651-be74-0a154c579424)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9f7389dd-70c6-40f1-b786-62df9debf0e8)


To define a port for a standard cell in the Magic layout tool, you can follow these steps:
1. In the Magic Layout window, start by sourcing the .mag file for your design, such as an inverter.
2. Go to the "Edit" menu and select "Text." This action will open a dialogue box for text editing.
3. When you double-click the 'S' key at the I/O labels on the layout, the text will automatically adopt the string name and size of the label.
4. Make sure to check the "Port enable" checkbox, and ensure that the "Default" checkbox is unchecked, as shown in the figure.

These steps will help you define a port for your macro cell when working with LEF files in Magic.
![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/2e5795dd-04a9-481c-9772-c5c6ac04b437)


Setting  port class and port use attributes for layout:
* Select port A in magic:
port class input
port use signal

* Select Y area
port class output
port use signal

* Select VPWR area
port class inout
port use power

* Select VGND area
port class inout
port use ground


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/ab1f2794-173b-4067-b986-fd33edc5e3de)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/898022f9-729d-4569-8ab8-7fa144438783)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/c0dc2345-b727-4464-9b39-71f1f39a0727)


Lef Extraction: 
1. Using the Tkcon window, assign the name "sky130_vsdinv.mag" to your custom cell.
2. To generate the LEF file, execute the command: "lef write."
3. This action will result in the creation of the "sky130_vsdinv.lef" file.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/755710e1-ada3-4cfc-bc6e-1c3c7d8c2278)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/266a05fe-9030-42fe-b380-639918a8e85d)


#### To include a custom standard cell in an ASIC design, you can follow these steps:

1. Create the Custom Standard Cell:
        Design your custom standard cell, such as an inverter, using a layout editor like Magic or your preferred ASIC design tool.
2. Copy Library Files:
        Locate the necessary library files (LEF and LIB files) related to your custom cell and the standard cell library. In your case, you mentioned these files: "sky130_fd_sc_hd_typical.lib," "sky130_fd_sc_hd_slow.lib," and "sky130_fd_sc_hd_fast.lib."
3. Copy these library files along with your custom cell LEF file to a suitable directory, typically referred to as your ASIC design project's "src" folder.
4. Modify config.tcl:
         Open the "config.tcl" file in your ASIC design project.
Add or modify the library definitions to include the paths to your custom cell library files and your custom cell's LEF file. 

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/cacc2630-8790-41da-9f1f-dad5de2e9be1)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/15f42b05-0536-42ed-a77e-3ccfd7e9b654)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/ade7c5b5-7e24-4747-a4ed-f68bd19d4d29)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/89739593-0672-42a3-8496-178178ad9cd0)


</details>


<details>
 <summary> Post-synthesis timing analysis Using OpenSTA  </summary>



</details>

<details>
 <summary> Clock Tree Synthesis using Tritoncts </summary>



</details>

### Day 5


<details>
 <summary> Final Steps in RTL2GDS  </summary>

 ### Maze Routing and Lee's Algorithm

Routing is a crucial step in electronic design, where the goal is to establish physical connections between two pins while ensuring a valid and efficient path. Various algorithms have been developed for routing tasks, and one notable approach is the Maze Routing algorithm, which includes Lee's Algorithm.

In the Maze Routing algorithm, a grid, akin to the one used during cell customization, is employed to facilitate routing. This approach begins with two key points: the source and the target. The Lee algorithm, a specific instance of Maze Routing, leverages this grid to identify the shortest and most optimal route between these two points.

The algorithm operates by assigning labels to neighboring grid cells around the source, incrementing these labels progressively from 1 until it reaches the target (e.g., from 1 to 7). During this process, various paths may emerge, including L-shaped and zigzag-shaped routes. Lee's Algorithm is designed to prioritize selecting the best path, often favoring L-shaped routes over zigzags. In cases where L-shaped paths are not available, the algorithm may resort to zigzag routes. This approach proves particularly valuable for tackling global routing tasks.

However, it's essential to acknowledge that the Lee algorithm has its limitations. It essentially constructs a maze and then numbers its cells from the source to the target. While effective for routing between two pins, it can become time-consuming when dealing with a large number of pins or complex layouts. In such scenarios, alternative routing algorithms designed to address similar challenges may be more efficient and practical.

In summary, Maze Routing, with Lee's Algorithm as one of its representatives, is a valuable approach for solving routing problems by finding optimal paths between source and target pins. Nonetheless, it's important to consider the specific requirements and complexity of the routing task to determine the most suitable algorithm for the job.

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/f21b2b68-3bf4-4f58-9668-456dde193305)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/1f618de9-ea81-47c6-a0c7-d09673ba5b4e)

* Design Rules for Physical Wires:

    * Minimum Width of the Wire: This rule specifies the smallest permissible width for a wire in the design. Ensuring that wires meet this minimum width is essential for guaranteeing signal integrity, power distribution, and manufacturability.

    * Minimum Spacing Between the Wires: DRC defines the minimum separation allowed between adjacent wires. Adhering to this rule helps prevent issues like crosstalk and short circuits caused by wires being too close to each other.

    * Minimum Pitch of the Wire: The pitch of a wire refers to the center-to-center spacing between identical wires in a regular pattern. DRC sets a minimum pitch requirement to optimize chip density and maintain manufacturability.

* Solving Signal Short Violations:

In cases where DRC identifies signal short violations, a common technique is to use additional metal layers. This involves routing wires on an upper metal layer to address the violation. Key considerations include:
* Metal Layer Selection: Choosing the appropriate metal layer to reroute the wire to, ensuring it does not interfere with other design elements.

* Via Rules: DRC also checks the design's via rules, including the via width and via spacing. Via rules govern how vias (connections between different metal layers) should be designed and placed to maintain signal integrity and avoid manufacturing issues.

</details>


<details>
 <summary> Power Distribution Network generation </summary>

In OpenLANE, the process of generating the Power Distribution Network (PDN) differs from the general ASIC (Application-Specific Integrated Circuit) design flow. Unlike the traditional flow, PDN generation is not part of the floorplan phase. Instead, it occurs after Clock Tree Synthesis (CTS) and post-CTS Static Timing Analysis (STA).

To check whether the PDN has been created, you can verify the current design environment variable using the following command:
```
echo $::env(CURRENT_DEF)
```
This command will display the current design definition (DEF) file that is being used in your OpenLANE session. If a PDN has been generated for your design, it will be reflected in the DEF file.

Here are the steps involved in generating the PDN in OpenLANE:
1. Prepare the Design:
    Use the prep command to prepare your design. In this example, the design is named "picorv32a," and a specific tag "Run 12.07.10.11" is used for version control or tracking purposes:

``` 
prep -design picorv32a -tag "Run-------"
```
Generate the Power Distribution Network (PDN):
After the design is prepared, you can proceed to generate the PDN using the gen_pdn command:

```
gen_pdn
```
The gen_pdn command initiates the generation of the Power Distribution Network, ensuring that power is distributed efficiently and reliably throughout the chip.


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/519ac8f4-b4a2-447b-bd6b-184f62891d2e)

Layout in magic tool post routing:
![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e71b218c-a58b-4915-adbd-71961885b9bb)


</details>


<details>
 <summary> Routing </summary>

#### Routing Stages in Electronic Design Automation (EDA) Tools

In the field of Electronic Design Automation (EDA) tools, routing processes, such as those in OpenLANE and commercial EDA tools, are highly complex due to the vast design space. To manage this complexity, the routing procedure is typically divided into two distinct stages: Global Routing and Detailed Routing. These stages are handled by specific routing engines.

1. Global Routing:
In the initial Global Routing stage, the routing region is divided into rectangular grid cells and represented as a coarse 3D routing graph. This task is efficiently executed by the "FASTE ROUTE" engine. The primary goal of Global Routing is to create a high-level routing plan for the chip.

2 .Detailed Routing:
The subsequent Detailed Routing stage involves working at a finer grid granularity and employing routing guides to implement the physical wiring. This stage is managed by the "tritonRoute" engine. While "Fast Route" generates initial routing guides, "Triton Route" refines the routing further. It utilizes the information obtained from Global Routing and applies various strategies and optimizations to find the most optimal paths for connecting the pins.

Key Features of TritonRoute:

1. Initiating Detailed Routing: TritonRoute serves as the starting point for the detailed routing process, laying the foundation for subsequent routing steps.
2. Adherence to Pre-Processed Route Guides: TritonRoute places significant emphasis on following pre-processed route guides, which involves several actions:
3. Initial Route Guide Analysis: TritonRoute carefully analyzes the directions specified in the preferred route guides. If any non-directional routing guides are identified, it breaks them down into unit widths for routing clarity.
4. Guide Splitting: In cases where non-directional routing guides are encountered, TritonRoute divides them into unit widths to facilitate the routing process.
5. Guide Merging: TritonRoute streamlines routing by merging guides that are orthogonal or touching the preferred guides.
6. Guide Bridging: When TritonRoute encounters guides that run parallel to the preferred routing guides, it utilizes an additional layer to bridge them, ensuring efficient routing within the preprocessed guides.

Assumption of Route Guide Compliance: TritonRoute operates on the assumption that route guides for each net satisfy inter-guide connectivity. These guides can be on the same metal layer with touching guides or neighboring metal layers with nonzero vertically overlapped areas (vias are placed accordingly). Additionally, each unconnected terminal, such as a pin of a standard cell instance, should have its pin shape overlapped by a routing guide, typically denoted as a black dot (pin) within a purple box (metal1 layer).

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/869cd3e1-0f33-4437-ad1e-2dd8f5f550ac)



</details>


## Word of Thanks
I sciencerly thank **Mr. Kunal Ghosh**(Founder/**VSD**) for helping me out to complete this flow smoothly.

  
## Reference 
- https://www.vsdiat.com
- https://github.com/nickson-jose/vsdstdcelldesign/
- http://opencircuitdesign.com/magic/
- https://skywater-pdk.readthedocs.io/en/main/
