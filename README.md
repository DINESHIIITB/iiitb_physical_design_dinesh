# iiitb_physical_design_dinesh


[week 0](#week_0)

[Day 0](#day-0)

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


Reduced Instruction Set Computer (RISC)

RISC-V is an open-source instruction set architecture (ISA).An instruction set architecture defines the set of instructions a processor can execute. RISC-V offers multiple base instruction sets (RV32I, RV64I, etc.) and optional standard extensions (e.g., M for integer multiplication/division, F for single-precision floating-point, D for double-precision floating-point, and more). This modularity allows designers to tailor the architecture to their specific needs.

Compilation: Use a C compiler (e.g., GCC, Clang) to compile the C source code into assembly code. The compiler translates the high-level C code into low-level assembly code that the hardware can understand.

Assembly: Assemble the generated assembly code using an assembler (e.g., GNU Assembler - GAS). The assembler converts the assembly code into machine code, which consists of binary instructions that the hardware can directly execute. The type of instructions depend on what type of hardware it is, if it is risc v then the instructions are also risc v.

Loading: Load the generated executable binary onto the target hardware. This can involve transferring the binary to a microcontroller, FPGA, or other hardware platform via appropriate interfaces (e.g., JTAG, USB, SD card).

Execution on Hardware: Run the program on the target hardware. The hardware's CPU fetches and executes the machine code instructions, carrying out the logic specified in the C source code.





![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/f3d963b3-c93e-4e94-9d33-a852e837ab47)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/c08f0252-fc86-4b41-868f-327212a3da2b)

</details>


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/2c65706f-9725-4e2f-a8e9-0f3c0d518992)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/6312baa3-4225-4c02-810d-af8f313de0f0)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/04408220-cf7b-463c-a6f2-a5575afa113c)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/d56920d8-aa12-4a39-b85c-fb2677f563f3)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9bd7cc3c-1cb1-4a2a-8039-e8512d6db6b2)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/9c724efe-34a6-4e24-b818-8297a0e4eb3e)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/b69b48da-4b80-451a-8b2d-d7470b522de1)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/a8ff07b6-b657-4a88-b650-ac83654c7255)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/e2bed2d2-389c-4e23-b45e-983fab17b5c4)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/29d3e2f4-e1bd-4cf6-851a-dec4f5c7fb9a)

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/08145132-edf3-4b41-a3a1-54c98ab2bf44)


![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/85e26eab-e126-4d17-aeed-17ed65cbe596)


signoff

![image](https://github.com/DINESHIIITB/iiitb_physical_design_dinesh/assets/140998565/54272ca3-7de1-4a92-9310-10730a8dd5c9)
















