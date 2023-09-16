# iiitb_physical_design_dinesh


[week 0](#week_0)

[Day 0](#day-0)

[Day 1](#day-1)

# week_0

## Day 0

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


## Day 1

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





</details>



<details>
 <summary> General timing characterization parameters </summary>





</details>

### Day 3

### Design library cell using magic layout and ngspice characterization 

<details>
 <summary> Labs for CMOS inverter ngspice simulations </summary>


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





</details>





