# IIITB_ASIC_course
[Day 0 : Open Source Labs installation](#day-0)

[Day 1 : Introduction to Verilog RTL design and Synthesis](#day-1)

[Day-2-Timing libs,hierarchical,flat synthesis,efficient flop coding styles](#Day-2-Timing-libs-hierarchical-flat-synthesis-efficient-flop-coding-styles)

## Day 0

<details>
 <summary> Summary </summary>
	
I installed the needed tools.

</details>	


 <details>
 <summary> Yosys </summary>

  installed Yosys using the following commands:
```bash
git clone https://github.com/YosysHQ/yosys.git
cd yosys-master 
sudo apt install make 
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make 
sudo make install
```


Below is the screenshot showing sucessful launch:
![yosys](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/967f89e8-0e0d-4e28-a24c-a85ad2520cf5)
</details>

 <details>
 <summary> OpenSTA </summary>


 I installed and built OpenSTA (including the needed packages) using the following commands:
 ```bash
sudo apt-get install cmake clang gcctcl swig bison flex
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
```


Below is the screenshot showing sucessful launch:
![OpenSTA](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/1d4b793e-498f-4ac6-8981-cfdea8d1b33d)
</details>

<details>
 <summary> ngspice </summary>


 I downloaded the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory and unpacked it using the following commands:
 ```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install
 ```


Below is the screenshot showing sucessful launch:
![nglspice](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/57f96899-9ed5-43cf-8571-ee7c177c5917)

</details>

 <details>
 <summary> iverilog </summary>


 I installed iverilog using the following command:
  ```bash
sudo apt-get install iverilog
 ```


Below is the screenshot showing sucessful launch:
![iverilog](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/69ed4471-0d9d-4b25-8161-d71d32620453)

 </details>
 
 <details>
 <summary> gtkwave </summary>


 I installed gtkwave using the following command:
  ```bash
sudo apt-get install gtkwave
 ```


Below is the screenshot showing sucessful launch:
![gtkwave](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/9ac6cf97-74f6-4102-908c-5a26d788bd71)



</details>
 <details>
 <summary> magic </summary>


 I installed magic using the following commands:
  ```bash
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
 ```

Below is the screenshot showing sucessful launch:
 ![magic](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/caf7d981-6c27-4de9-a8e2-c01cc286a0cc)>




</details>


 <details>
 <summary> OpenLane </summary>


 I installed OpenLane using the following commands:
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git

sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io

sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 

docker run hello-world

Below is the screenshot showing sucessful launch:
 ![OpenLane](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e35808de-44e9-41c5-86d2-6e29f90b6623)


</details>


# Day 1

<details>
  <summary>Simulation</summary>
  
  **Simulator:** It is a tool for checking the design written in HDL. RTL design is checked for the the adherence to to spexifaction of required circuit.
 
  **Design:** It is the verilog code to create the circuit that meets the required specificaations. It involves using HDL to specify behaviour and structure of the circuit.
	
 **RTL design outline:**

	module module_name (port_list);
		//declarations;
		//initializations;
		//continuos concurrent assigments;
		//procedural blocks;
	endmodule
 
  **Testbench:** It is used to apply stimulus to the design to check the working of the circuit and ensure that it's functionality meets the required specifications. 

![TB](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/85e33863-e4f5-4918-8dbc-81d89d5a774b)

**iverilog:** iverilog stands for Icarus Verilog. Icarus Verilog is an implementation of the Verilog hardware description language.

**GTKwave:** GTKWave is a fully featured GTK+ based wave viewer for Unix, Win32, and Mac OSX which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing. 
![gtkwave](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/0abe95fa-d578-4d02-bce4-196dc23e989b)

### Lab examples using iverilog and GTKwave

In this lab session we were made familiar with the linux operating system as well as GTKwave along with codes in iverilog. We cloned sky130RTLDesign library from github using command: **git clone**. and worked on good_mux file.

![Day1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/d33f5d3e-2de2-4b0d-a0db-9af14ba79baf)

![Day1_!](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/3686cea5-c028-4e23-8075-e18e984bed00)

![Day1_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/b59f444c-4007-49da-b36c-04eb0f3ac831)

![Day1_gtkout](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/8bef8ca6-7847-43ae-a51e-bb46e22ee0ac)

Here is the code used in todays lab :<br />

	module good_mux (input i0 , input i1 , input sel , output reg y); 
		always @ (*)
		begin
			if(sel)
			y <= i1;
			else 
			y <= i0;
		end
	endmodule


	`timescale 1ns / 1ps
	module tb_good_mux;
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;
      		// Instantiate the Unit Under Test (UUT), name based instantiation
		good_mux uut (.sel(sel),.i0(i0),.i1(i1),.y(y));
		//good_mux uut (sel,i0,i1,y);  //order based instantiation
	initial begin
		$dumpfile("tb_good_mux.vcd");
		$dumpvars(0,tb_good_mux);
		// Initialize Inputs
		sel = 0;
		i0 = 0;
		i1 = 0;
		#300 $finish;
	end
	always #75 sel = ~sel;
	always #10 i0 = ~i0;
	always #55 i1 = ~i1;
	endmodule

</details>  

<details>
 <summary> Synthesis </summary>

 **Synthesizer:** It is a tool used to convert RTL design to gate level netlist. The Synthesis tool used in this lab is yosys.
 
 **Netlist:** It is representation of RTL design in for of standard cells i.e. It is a properly implemented chip design in terms of logic gates.
![netlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/3ab88731-8950-4a71-99ee-afcd24a65a91)

 Synthesis takes place in following steps:
- Converting RTL into simple logic gates.
- Mapping those gates to actual technology-dependent logic gates available in the technology libraries.
- Optimizing the mapped netlist keeping the constraints set by the designer intact.

- **Verification of Synthesized design**: In order to make sure that there are no errors in the netlist, we need to verify the synthesized circuit. The netlist verification flow can be seen in the below image:
![synthesis](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/c6635052-d022-48f8-a760-83b44f080f0a)

  **Yosys**:It is a framework for RTL synthesis. It provides a basic set of synthesis algorithms for various application domains. Yosys is the core component of most our implementation and verification flows.
  ![yosys netlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/6354825e-fd96-4c83-89f5-bd5f73376b28)

Below are the commands to perform above synthesis.

- RTL Design  - read_verilog
- .lib        - read_liberty
- netlist file- write_verilog
![yosys](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/da64a716-315d-4163-bbd4-fcf8d4510a51)

![synth_netlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/36b0bdb8-4612-4d0e-878b-a35ca94edd73)

![synth_nnetlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/af7441fe-c0ae-4722-91ea-bb7f94cd655e)

**.lib :** It is a collection of logical modules like logic gates. It contains cells with different sppeds, no. of inputs etc. that can be used as required.
![sunthsize](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/bf761a83-9614-4364-81b7-113a8e43d513)

**Need for different speed of gates:**
  
  ![COMBI](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/57448e7a-781c-4b94-b18f-22b0b521b539)
   - We need gates fast enough so that the total delay of all the gates is smaller than the T(clk).
   
     ![tclk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/babb72d3-f561-4782-97f5-cf591001b54c)
   - If we want to capture B in next clock cycle rather than the same, we need to make the delay larger than the whole time, so some cells need to work slowly

**Fast cell VS slow cells:**
- A load in digital logic is a capacitor
- A faster charging or discharging means less delay
- To increase the rate of charging or discharging we need to widen the transistors.
- Wider transistor gives lower delay: but more is required and more power is required
- Narrow transistors give out more delay  : we need less area and less power is consumed.

</details> 


# Day-2-Timing libs, hierarchical, flat synthesis, efficient flop coding styles
<details>
<summary>Introduction to timing .libs</summary>
 </details> 
