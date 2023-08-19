# IIITB_ASIC_course
- [Day-0-Installation](#day-0)

- [Day-1-Introduction to Verilog RTL design and Synthesis](#Day-1)

- [Day-2-Timing libs,hierarchical,flat synthesis,efficient flop coding styles](#day-2)

- [Day-3-Combinational and sequential optmizations](#day-3)

- [Day-4-GLS, blocking vs non-blocking and Synthesis-Simulation mismatch](#5-day4)

- [Day-5-if, case, for loop and for generate](#day-5)

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


## Day 2
<details>
 <summary> Summary </summary>
 I first synthesized a multiple module (made of two submodules) at the multiple module level 
 (both in hierarchical and flattened forms) then at the submodule level. Synthesis at the 
 submodule level is important for two reasons: 1-) when we have multiple instances of same module 
 (we synthesize once and replicate this netlist multiple times and stitch together the replicas 
 to get the multiple module netlist, and 2-) when we want to divide and conquer (in massive 
 designs) so that the tool can generate a portion by portion of the overall netlist and then we 
 can stitch together the netlist portions to get the multiple module netlist. After that, I 
 sumulated the different flop designs using iverilog and gtkwave, then synthesized the designs. 
 Finally, I synthesized 2 designs that were special; their synthesis used optimizations.
</details>
<details>
 <summary> Introduction to .lib </summary>
Under this section, we get a better insight regarding .lib. We have the general overview that it 
stores the models of all the standards cells, various variations and flavours as per the need of 
specification provided. Getting an insight into the .lib file, we start with the file name -

sky130_fd_sc_hd__tt_025C_1v80  
The name sky130 represemts that the library is based on 130nm technology. Under the nomenclature, we define PVT - process, voltage and temperature. Process refers to the variations due to the fabrication, ie. there will variations in the silicon fabricated even by the same machine. There is variation due to the voltage and temperature as well. Silicon is very sensitive to temperature. All these 3 determines how the silicon is going to perform. We aim to design such that silicon works in all the conditions, across various variations. These three are indicated under the name, tt stands for typical process, 25c indicates the temperature - 25C and 1v80 indicates the voltage of 1.80volts. It is to be noted, all the models under the said library are designed for the given PVT parameters.

We open the .lib file using gvim to go through various other informations it provides.
![1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/cd132f8a-222e-4f38-9f23-9e445d4e168b)

- It defines the technology begin used "CMOS" and the delay model as "table_lookup"
- It defines the units for various parameters and quanities, such as, 1ns for time, 1V for voltage, 1mA for current, 1kohm for resistance and 1pF for capacitance.
- It defines the operating conditions as "tt_025C_1v80".

Considering a two input and gate, and compare different two input and gate.
![2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/37452e18-8db6-4529-8355-906f294b1a3d)

- The lib files conatins the power and timing information for the 4 possible outcomes.
- All three taken cells are 2 input and gates, but differ in their areas, and2_4 has a larger area than area2_2 and consequently more than and2_0.
- Having a larger area refers to the use of a wider cell. Wider cells will be faster, but consumes more power. This can be seen in the datials under the lib file.
</details>

<details>
<summary> Heirarchial vs Flat Synthesis </summary>
Under this section, we go over what is heirchial synthesis and flat synthesis. For this, we have taken the case of multiple_modul2s.v from verilog files to have a better unstanding.



```bash

```
![multiple_modules_net](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/475233e3-c6d5-4539-80d1-3c767c920f0c)

Gate level diagram

![3](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/30f490f1-01f5-40b2-a444-09385a1522d5)

We go to the directory where we find the model in verilog files
```bash
$ cd Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
$ yosys
read_liberty -lib ~/Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ~/Documents/ASICs/VLSI/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show multiple_modules
```
**Reading and Synthesis of the said module**

- we hit show and expect to attain a similar schematic we had drew
![multiple_modules](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/16ded881-6bc8-4fff-95fd-5f7a1ea5200a)


- We get the image of the top module.
- We don't get to see the and and or gates. We see the modules u1 and u2, which are the instances of the gates.
- **This type of design is called an heirarchial design.**
- 
The synthesizer considers the module hierarcy and does the mapping accordting to instantiation. Here is the hierarchical netlist code for the  multiple_modules:

	module multiple_modules(a, b, c, y);
		  input a;
 		 input b;
 		 input c;
		  wire net1;
 		 output y;
 	  sub_module1 u1 (.a(a),.b(b),.y(net1) );
	  sub_module2 u2 (.a(net1),.b(c),.y(y));
	endmodule
	
	module sub_module1(a, b, y);
 	 wire _0_;
 	 wire _1_;
 	 wire _2_;
 	 input a;
 	 input b;
 	 output y;
 	 sky130_fd_sc_hd__and2_0 _3_ (.A(_1_),.B(_0_),.X(_2_));
 	 assign _1_ = b;
 	 assign _0_ = a;
 	 assign y = _2_;
	endmodule

	module sub_module2(a, b, y);
  	wire _0_;
 	 wire _1_;
 	 wire _2_;
  	input a;
  	input b;
 	 output y;
 	 sky130_fd_sc_hd__lpflow_inputiso1p_1 _3_ (.A(_1_),.SLEEP(_0_),.X(_2_) );
 	 assign _1_ = b;
 	 assign _0_ = a;
 	 assign y = _2_;
	endmodule

Flattened netlist:

In flattened netlist, the hierarcies are flattend out and there is single module i.e, gates are instantiated directly instead of sub_modules. Here is the flattened netlist code for the  multiple_modules:

	module multiple_modules(a, b, c, y);
 		 wire _0_;
  		 wire _1_;
 		 wire _2_;
 		 wire _3_;
		 wire _4_;
		 wire _5_;
 		 input a;
 		 input b;
 		 input c;
 		 wire net1;
 		 wire \u1.a ;
		 wire \u1.b ;
		 wire \u1.y ;
		 wire \u2.a ;
		 wire \u2.b ;
 		 wire \u2.y ;
  		output y;
 		 sky130_fd_sc_hd__and2_0 _6_ (
  		  .A(_1_),
  		 .B(_0_),
   		 .X(_2_)
  		);
 		 sky130_fd_sc_hd__lpflow_inputiso1p_1 _7_ (
  		  .A(_4_),
 		  .SLEEP(_3_),
  		  .X(_5_)
 		 );
 		 assign _4_ = \u2.b ;
 		 assign _3_ = \u2.a ;
 		 assign \u2.y  = _5_;
 		 assign \u2.a  = net1;
		 assign \u2.b  = c;
 		 assign y = \u2.y ;
		 assign _1_ = \u1.b ;
		 assign _0_ = \u1.a ;
		 assign \u1.y  = _2_;
		 assign \u1.a  = a;
		 assign \u1.b  = b;
 		 assign net1 = \u1.y ;
		endmodule

The commands to get the hierarchical and flattened netlists is shown below:

**yosys> write_verilog -noattr multiple_modules_hier.v**

8. Executing Verilog backend.
Dumping module `\multiple_modules'.
Dumping module `\sub_module1'.
Dumping module `\sub_module2'.

**yosys> !gvim multiple_modules_hier.v**

11. Shell command: gvim multiple_modules_hier.v

**yosys> flatten**

12. Executing FLATTEN pass (flatten design).
Deleting now unused module sub_module1.
Deleting now unused module sub_module2.
<suppressed ~2 debug messages>

**yosys> write_verilog -noattr multiple_modules_flat.v**

13. Executing Verilog backend.
Dumping module `\multiple_modules'.

**yosys> !gvim multiple_modules_flat.v**

14. Shell command: gvim multiple_modules_flat.v

This is the synthyesized circuit for a flattened netlist. Here u1 and u2 are flattened and directly or gates are realized.

![flatten](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/44084c7b-2d36-41fc-9d4c-033adb546b0d)

Here is the synthesized circuit of sub_module1. We are also generating module level synthesis so that if there is a top module with multiple and same sub_modules, we can synthesize it once and can use and connect the same netlist multiple times in the top module netlist.

Another reason to generate module level synthesis and then stictch them together is to avoid errors in a top module if its massive and consists of several sub modules. Generating netlist for synthesis and then stiching it together in top level becomes easier and reduces risk of output mismatch.

We control this synthesis using **synth -top <module_name>** command

![sub_module1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/08fc21ee-23c4-49df-9327-307001012edb)


</details>
<details>
<summary> Various Flop coding styles and optimizations </summary>
Under this section, we go through all the various types of flops available and how to design and 
code them efficiently. All the required files are presen in the folder verilog_files.
To understand the need of flops, we refer the example of a simple circuit with delays as 2ns for 
and gate and 1ns for or gate.
 
![4](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/65401c06-ec16-49f6-874e-1600abc9b717)


- Considering the input goes from 0 to 1 for a and b and simultaneously, 1 to 0 for c.
- Ideally for the transition from (001) to (110), the output should have been a constant at 1,
but because of the delay, we get outout as 0 for a brief period of 2ns.
- This is called a glitch.
  
![5](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/4ad3c335-933a-49ad-8dbc-7fb64bf8bc1f)

- More the number of combinational circuits, more number of glitches appear, giving a glitchy output.
- To avoid this, we need an element to store the value. Comes the flops into picture.
- We use a D flipflop. They are a storage element. They are placed between combinational circuits and changes value only at clock edge.
![6](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/ab9145c0-096e-45c2-85ab-803bd5b645a6)

- We need to initailise the flops, else the combinational circuits gives a garbage value. For this purpose we have reset and set pins. They can be asynchoronous and synchronous.

Types of flops

- Flops can be designed to be asynchronous or synchronous. It depends on whether the flop is sensitive to the reset and set parameters.
- Under asynchronous, the flop is sensitive to the reset or set, ie the design checks for them and the moment, reset is encountered, the output is pulled to 0 irrespective of the clock. For asynchronous set, the output is pulled to 1.
- The circuit design and timing diagram along with verilog code is displayed under the image below under column 1.
- Under the case of synchronous reset, the output is pulled to 0 at the next clock cycle. The design and timing diagram along the verilog code is shown under the column 2 of the image below.
- Sync reset can be understodd as the input is pulled to 0, thus output becomes 0 for next clock cycle.

![7](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/18024a99-5be5-4403-88e4-50bcabfbe526)

Now, we go through simuations of async reset, async set and sync async reset and observe the waveforms using gtkwave to have a better understand.

**RTL code for dff_asyncres**
```bash
module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```
On execution of iverilog and gtkwave we get

![reset_async](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/20880ef4-5e33-4fc1-a9f5-dadd7dfcbc6e)
- We can observe that the output q goes to 0 when the reset is encountered.
- Now we synthesis the design using yosys.

![async_res](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/2e007031-48fd-459e-9f45-9529a4421380)

**RTL design of dff_async_set**
```bash
module dff_async_set ( input clk ,  input async_set , input d , output reg q );
always @ (posedge clk , posedge async_set)
begin
	if(async_set)
		q <= 1'b1;
	else	
		q <= d;
end
endmodule
```
- upon execution on terminal using iverilog and gtkwave
  
![set_async](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/21f6a434-c8dd-4d35-a753-857a7320bd67)

- We can observe that the output q goes to 1 as soon as we encounter the set irrespective of that clock. -Now we synthesis the design using yosys.
![async_set](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/d644d081-baa0-42a8-b3d0-a092a13164fb)

**RTL code for dff_syncres**
```bash
module dff_syncres ( input clk ,  input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if(sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```
- Upon executing iverilog and gtkwave
![sync_reset](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/da0ac16c-b5e6-44a9-8666-4fd78ab1bc75)
- It is observed that the output q is set to 0 at the next clock pulse when the reset is encountered, thus it is the case of sync reset.
- Now we synthesis the design using yosys.
![sync_res](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/29d29ab7-70ba-4c64-bce1-1becce5136e2)

</details>
<details>
<summary> Interesting Optimisations</summary>
Under this section we look into two interesting cases and how they are executed and designed.

First we look into mul2.v

- Code for mul2.v
```bash
module mul2 (input [2:0] a, output [3:0] y);
	assign y = a * 2;
endmodule
```
- The block diagram and the truth table for the executed logic is shown under.
![8](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/01e3ceb0-7407-49de-84cf-34c759ed0f9e)

- From these, we are able to infer that the logic requires the input to be multiplied with 2, and upon checking the output it is the input with 1'b0 padding.
- Thus the design for the logic needs no hardware to be mapped.
- We will confirm this using yosys.
![mul2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/c099c276-c82a-4c88-a800-bb16890a746f)

- From the yosys synthesis, we observe the number of cells in design is 0 and there is no hardware to be mapped. These have been highlighted in the picture above.
- The schematic attained shows a similar result.
- This was done in case of multiplication with 2. For multiplication with 4, we give 2'b00 padding and for 8, we give 3'b000 padding. This goes on.

Now, we look into another special case.

- Condider a 3bit number a[2:0], and the logic to be implemented is that the output y[5:0] is equal to 9 times of a[2:0].
- Code for execution
```bash
module mult8 (input [2:0] a , output [5:0] y);
	assign y = a * 9;
endmodule
```
- explanation
![9](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/6d99ea98-da02-45d0-b0ae-70a2d6fe163e)

- Multiplcation with 9 can be seen as multiplication with 8 and plus 1.
- We know multiplication with 8 is equal to 3'b000 padding, and adding the same 3 bit number to the padded number comes of as concatanation of {a,a}.
- Thus there are no standard cell required for the design. We verify this using yosys.


- We see that there are no standard cells required.
- We see the concatanation operation done in the netlist.
</details>




## Day 3
<details>
<summary> Summary </summary>
I have synthesized designs with optimizations. Combinational logic optimizations include 1-) 
constant propagation (when the combination is just propagating a constant) and 2-) boolean logic 
optimization (when boolean rules are used to simplify the expression). Sequential logic 
optimizations include 1-) sequential constant propagation (when constant is propagated with clock 
involved), 2-) state optimization (when unused states are optimized), 3-) retiming (when logic is 
split to decrease timing of the different logic portions and increase frequency), and 4-) 
sequential logic cloning (when physical aware synthesis is done to optimize the floop plan)
</details>
<details>
<summary> Introduction to Optimizations </summary>
Optimising the combinational logic circuit is squeezing the logic to get the most optimized digital design so that the circuit finally is area and power efficient. This is achieved by the synthesis tool using various techniques and gives us the most optimized circuit.

**Techniques for optimization for combinational logic**:

- Constant propagation which is Direct optimizxation technique
- Boolean logic optimization using K-map or Quine McKluskey

Here is an example for **Constant Propagation**
![1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/108502bc-a004-47fe-a54c-105d085f9ce7)
In the above example, if we considor the trasnsistor level circuit of output Y, it has 6 MOS trasistors and when it comes to invertor, only 2 transistors will be sufficient. This is achieved by making A as contstant and propagating the same to output.
**Techniquies for Sequentional logic otimizations**
Below are the various techniques used for sequential logic optimisations:
- Basic
   Sequential contant propagation
- Advanced
   State optimisation
   Retiming
   Sequential Logic Cloning (Floor Plan Aware Synthesis)

-  The input of D ff is grounded, ir d=0, and the reset parameter is given. Here even if the
  reset is given or not the output output of the flop is constant at 0, hence the overall outcome
  is constant.

![2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/370d4b89-5728-4518-a2a7-a5b3a73741ae)
- Now taking the same circuit, but instead of reset, we give set. Now when the set is 1, the flop
output follows set. As soon as set is removed, the output goes to 0 at the next positive clock
edge. Thus now we can't remove the flop from design, Thus we retain the flop.

![3](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7c729093-7648-4a04-b5db-6ff3f2c9eb56)
**Advanced Methods for Sequential logic Optimisation**

- State optimization in ASIC design is about finding the best trade-offs among performance, power
efficiency, area utilization, and other design objectives to create an effective and efficient
custom integrated circuit for a particular application.
- Re-timing is the technique used to optimize the timing performance of a digital circuit by
moving registers (flip-flops) to different locations within the circuit without changing its
functionality. The primary goal of retiming is to improve the critical path delay, which is the
longest path through the logic circuit that determines the maximum operating frequency.
- Sequential logic cloning or flip-flop cloning or state machine cloning is the technique used to
replicate or duplicate certain portions of sequential logic circuits. This technique is employed
to improve performance, reduce critical path delays, or optimize power consumption in a design
without altering its functional behavior.



</details>
<details>
<summary> Combinational logic optimizations </summary>

Let's consider an example concurrent statement assign **y=a?(b?c:(c?a:0)):(!c)**

The above expression is using a ternary operator which realizes a series of multiplexers, however, when we write the boolean expression at outputs of each mux and simplify them further using boolean reduction techniques, the outout y turns out be just **~(a^c)**

Command to optimize the circuit by yosys is
```bash
yosys> opt_clean -purge
```
opt_clean remove unused cells and wires. The -purge switch removes internal nets if they have a 
public name. This command identifies wires and cells that are unused and removes them. This 
command can be used to clean up after the commands that do the actual work.



In case of multiple models, it is important to flatten the design then followup with 
optimization.

**Lab 1-opt_check.v**
**RTL code**
```bash
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```
- after synthesis on yosys
![opt_check](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/f30c2c9b-dc79-4dc2-9544-24cef7269776)

**Lab_2 opt_check2.v**
**RTL code**
```bash
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
- Hardware after synthesis on yosys
![opt_check_2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/f2d32f8b-0eb2-4dd7-a6b2-f452fbfa2ba9)

**Lab_3 opt_check3.v**
**RTL code**
```bash
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
- hardware after synthesis on yosys

![opt_check_3](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/096040ba-caf5-4609-b28b-78bc0df9da47)

**Lab_4 opt_check4.v**
**RTL code**
```bash
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```
- Hardware  after synthesis on yosys

![opt_check_4](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/43a1707d-0ee9-4ceb-8843-18932d676c90)
**Lab_5 multiple_module_opt.v
**RTL code**
```bash
module sub_module1(input a , input b , output y);
 assign y = a & b;
endmodule


module sub_module2(input a , input b , output y);
 assign y = a^b;
endmodule


module multiple_module_opt(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
sub_module2 U3 (.a(b), .b(d) , .y(n3));

assign y = c | (b & n1); 


endmodule
```
- Hardware after synthesis on yosys
- 
![multiple_module_opt_](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/1727b12b-74a4-45eb-8c18-1593513af53b)
- Hardware after clean :
- ![multile_module](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/33c30475-3cc1-4888-8b47-392ede75b4a8)
- 

**Lab_6 multiple_modules_opt2.v**
**RTL code**
```bash
 module sub_module(input a , input b , output y);
 assign y = a & b;
endmodule



module multiple_module_opt2(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
sub_module U2 (.a(b), .b(c) , .y(n2));
sub_module U3 (.a(n2), .b(d) , .y(n3));
sub_module U4 (.a(n3), .b(n1) , .y(y));


endmodule
```
- Hardware after yosys synthesis
![multiple_module_opt_2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/c97be23c-1c8a-474b-8ef1-464e117b409e)

- Harware after clean
-![multile_module_2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/506e9f0f-c8ca-4382-9665-db49c2d1b15d)
 
</details>

<details>
<summary> Sequentional Logic Optimizations </summary>

**Lab_1 dff_const1.v**
**RTL code**
```bash
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
```
- Simulation on iverilog and gtkwave
- 
![dff_const1_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/169586bf-4382-4d5e-9578-c765acbec8a0)

- optimization using yosys

![dff_const1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/94718ab3-b6fb-4bdb-a0ab-74a8394cea25)


**Lab_2 dff_const2.v**
**RTL code**
```bash
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end

endmodule
```
- Simulation using iverilog and yosys

![dff_const2_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/65fb4d37-79cc-4db0-b7d4-9ee9e7bd5c40)

- optimization using yosys

![dff_const2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/6739d434-9cae-47ec-9d56-6e087e971021)


**Lab_3 dff_const3.v**
**RTL code**
```bash
module dff_const2(input clk, input reset, output reg q);
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
-simaulation using iverilog and gtkwave

![dff_const3_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7acdd5a0-7ce5-4e9c-8f79-cb605c603105)

-optimization using yosys

![dff_const3](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/05db8912-0840-42f9-a4d4-3006a4804bd2)


**Lab_4 dff_const4.v**
**RTL code**
```bash
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
-Simulation using iverilog and gtkwave

![dff_const4_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e28eb6cb-bd20-4460-bfe9-db289273de7f)

-optimization using yosys

![dff_const4](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/d3cb3001-1265-4a36-8d1a-bb34186cbaec)


**Lab_5 dff_const5.v**
**RTL code**
```bash

module dff_const5(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b0;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
-simulation using iverilog and gtkwave

![dff_const5_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/6eb1877e-c123-49df-83aa-0164cbc2646b)


-optimization using yosys

![dff_const5](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/253a8968-4cbb-4f6e-b909-f1d6d8a4ebd0)

</details>

<details>
<summary> Sequential optimizations for unused outputs </summary>
Under this section, we look into how yosys synthesizer optimises the design in case of unused 
bits in the output. For this we have taken a 3 bit counter. In case 1, only the LSB is taken as 
final output, thus the first two are left unused. In case two, we take the entire 3 bits as 
output.

 
![4](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/42b996a2-1902-4adc-8f49-c6ec7810af12)

**Lab_1 using count[0]**
**RTL code**
```bash
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
-synthesis using yosys

![counter](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/0b587918-b54e-4380-861c-f307300b492b)

**Lab_2 using all three bits count[2] and count[1] and count[0]
**RTL code**
```bash
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[2:0] == 3'b100;

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end
```
- synthesis using yosys

![counter2](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/029ed754-67cd-4e53-bae4-564423de681a)

- In the yosys generation, we see the design has encorporated 3 dff for the 3 bit counter.
- It is evident that the yosys synthesizer optimizes for the unsed bits in the output. This so important as illustrated because it saves a ton of space, and speed, and improves efficiency of the final design.
 </details> 

## Day 4
<details>
<summary> Summary </summary>
performed Gate Level Simulation (GLS). GLS is when the testbench is run with the netlist as 
design under test to ensure there are no synthesis and simulation mismatches, and it is important 
as it 1-) verifies the logical correctness of the post-synthesis design and 2-) ensures the 
timing of design is met. Synthesis and simulation mismatches can happen due to a lot of reasons 
including missing sensitivity list (some signal changes are not captured by the circuit because 
they are missing from the sensitivity list), blocking vs non-blocking assignments (inside an 
always block, "=" statements inside it are blocking meaning they are executed in order they are 
written, assignments (<=) on the other hand are non-blocking so they are executed in parallel => 
non-blocking should be used with sequential circuits. Note that the synthesis will yield same 
circuit with blocking and non-blockin; it will yield what would be obtained as if the statements 
where written in non-blocking format, so in case they weren't written as such a mismatch will 
occur with the simulation), and non-standard verilog coding.
</details>

<details>
<summary> GLS, Synthesis-Simulation mismatch and Blocking,Non-blocking statements </summary>
**GLS concepts and flow**
What is GLS-Gate Level Simulation?
GLS is generating the simulation output by running test bench with netlist file generated from 
synthesis as design under test. Netlist is logically same as RTL code, therefore, same test bench 
can be used for it.

Why GLS?
We perform this to verify logical correctness of the design after synthesizing it. Also ensuring 
the timing of the design is met.

Below picture gives an insight of the procedure. Here while using iverilog, we also include gate 
level verilog models to generate GLS simulation.

![1](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/88cbb13e-655c-43ef-be25-a53e0bf026c1)


**Synthesis Simulation Mismatch**
There are three main reasons for Synthesis Simulation Mismatch:
      -Missing sensitivity lis in always block
      -blocking vs non-blocking assignments
      -Non standard verilog coding
*Missing Sensitivity List*
To understand this we use examples for a mux with different sensitivity

-Code 1
```bash
module mux1 (input sel , i0, i1 ,
output reg y);

always@(sel)
begin
if(sel)
	y=i1;
else
	y=i0;
end

endmodule
```
-Code 2
```bash
module mux (input sel , i0, i1 ,
output reg y);

always@(*) 
begin
if(sel)
	y=i1;
else
	y=i0;
end

endmodule
```
- Mux 1 is sensitive to changes is changes in latches, ie the output y will change only at the changes of sel. Thus the changes of inputs i1 and i0 are not displayed in the output.
- Mux 2 is sensitive to all three, so when high sel, output covers all changes in i1, and for low sel, all changes in i0 are covered.
- Now, the simulation and synthesis of mux 2 wont have any mismatch.
- But mux1 will have mismatch,as simulators work on sensitivity list and the simulation will behave as a double edge triggered latch, while the synthesizer converts the logic into netlist and doesn't look into sensitivity list, thus synthesis will behave as a 2 input MUX.

*Blocking and Non-blocking statements*
Blocking statements execute the statemetns in the order they are written inside the always block. 
Non-Blocking statements execute all the RHS and once always block is entered, the values are 
assigned to LHS. This will give mismatch as sometimes, improper use of blocking statements can 
create latches.
</details>
<details>
<summary> Lab- GLS Synth Simulation Mismatch </summary>

**Lab_1 ternary_operator_mux.v**
**RTL code**
```bash
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
endmodule
```
- Simulation using iverilog and yosys

![ternary_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/72488d93-aa57-4d3f-9430-cb6f7b1d364c)

- now we synthesis using yosys

![ternary_sunth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e693d8e5-a174-4f4c-9cc8-c80282f1af67)

- generated netlist

![ternary_nelist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/0c390be6-8224-41a6-82d7-72c087f1a17f)

-Running GLS using the netlist file generated during yosys

![ternary_gtk_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/91066c8c-9f37-47d1-8d82-e147bef4bad5)

**it is clear that both simulatons are same**

**Lab_2 bad_mux.v**
**RTL code**
```bash

module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```
- Simulation using iverilog and gtkwave
- 
![bad_mux_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/11aa06e2-dde4-4023-8aff-65dd45bf4185)

- synthesis using Yosys

![bad_mux_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/65d0ca6a-fc7a-4951-8b0e-0bd66ac70ba0)

- netlist generated during synthesis

![bad_mux_netlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/0c300805-30f9-4a70-897d-6340646bb0a4)

- Running GLS using netlist file generated during yosys

![bad_mux_gtk_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/3233f59e-dac8-4684-be67-948d4153f3b7)

- Under this, we see a clear mismatch between the simulation and synthesis designs. The RTL file
and netlist files aren't the same logic implemention. This happened due to the sensitivity
listing under the RTL file.
</details>
<details>
<summary> Lab on Synthesis_Simulation Mismatch and Blocking </summary>
In thissection we willlook into the mismatch between simulation and synthesis caused due to the blocking statements.
	
**RTL code**
```bash
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c;
	x = a | b;
end
endmodule
```
- Running the simulation using iverilog and gtkwave
- 
![blocking_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7dae485c-d427-4ee3-963b-bea09ebc5c09)

- Synthesis using yosys

![blocking_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/1712e18d-97ad-481a-a6b9-eb658de3792b)

- Netlist generated

![blocking_netlist](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/eff81c84-e7a4-4ea6-a761-ad1af530a406)

- Running GLS on the netlist file generated using iverilog and gtkwave

![blocking_gtk_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/5e0c361a-1dc4-425f-b4a3-9e9e8b7befd9)
  
- It is seen that the waveform matches with the expected output for d=((a|b).c).
- There is clear mismatch between the simulation and synthesis in this case. This happended coz
we used blocking statements, and while simulation, the design makes a flop, which wasn't the
intention of the original design.
</details>


## Day 5

<details>
<summary> Summary </summary>
I have first learned about "if" and "case" statements which are used inside always blocks.
</details>
<details>
<summary> If and Case constructs </summary>
	
***if costruct***
The construct *if* is mainly used to create priority logic. In a nested if else construct, the 
conditions are given priority from top to bottom. Only if the condition is satisfied, if 
statement is executed and the compiler comes out of the block. If condition fails, it checks for 
next condition and so on as shown below.
**Syntax for nested if else**
```bash
if (<condition 1>)
begin
-----------
-----------
end
else if (<condition 2>)
begin
-----------
-----------
end
else if (<condition 3>)
.
.
.
```
**Dangers of *if* construct**
If use a bad coding style i.e, using incomplete if else constructs will infer a latch. We 
definetly don't require an unwanted latch in a combinational circuit. When an incomplete 
construct is used, if all the conditions are failed, the input is latched to the output and 
hence we don't get desired output unless we need a latch.

![image0 (1)](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7455994e-d542-4fa9-bedb-cc0c9af749a0)

***Case construct***
**syntax**
```bash
case(statement)
  case1: begin
       --------
	 --------
	 end
 case2: begin
	     --------
	 --------
	 end
 default:
 endcase
```
In case construct, the execution checks for all the case statements and whichever satisfies the 
statement, that particular statement is executed.If there is no match, the default statement is 
executed. But here unlike if construct, the execution doesn't stop once statement is satisfied, 
but it continues further.

**Caveats in Case**
Caveats in case occur due to two reasons. One is **incomplete case statements** and the other is **partial assignments in case statements**.
</details>
<details>
<summary> Lab on Incomplete *if*</summary>

**LAB_1 incomp_if**
**RTL code for incom_if.v**
```bash
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
end
endmodule
```
- simulation using iverilog and gtkwave
- 
![incomp_if_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/810d00db-4919-4296-a308-9e17eef57faa)

- synthesis using yosys

![incomp_if_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/ae879b4c-ec88-4f3b-bd84-a03c44774242)

- It is seen that there has been an inferred latch formation due to incomplete if-else
condtional statements.

**LAB_2 incomp_if2**
**RTL code for incomp_if2.v**
```bash

module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

end
endmodule
```
- Simulation using iverilog and gtkwave
- 
![incomp_if2_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/ecb96cfa-65dc-4eb9-aa10-794aa6a12142)

- Synthesis using yosys
- 
![incomp_if2_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/1ffda967-f8a9-42dc-bf4b-3ab95ed0d06d)

- It is seen that there has been an inferred latch formation due to incomplete if-else
condtional statements.

</details>
<details>
<summary> LAB on **case** construst </summary>
Here we'll look into various situations with case statement under simulation and synthesis

**LAB_1 wihout default**
We look into the formation of inffered latcg due toomission of default case.

**RTL code for incomp_case.v**
```bash
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
	endcase
end
endmodule
```
- Running RTL simulation using iverilog and gtkwave

![incomp_case_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7ac14711-be05-4f74-b0e3-0cb7876148ed)

- synthesis using yosys
  
![incomp_case_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/375ecdf4-f409-4bc9-af69-fa5b01d06453)

- It is seen due to omission of default case we have an inferred latch in hardware design

  **LAB_2 with default**
  We'll look into how default cae removes the frmation of a latch

  **RTL code for comp_case.v**
  ```bash
  module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
  always @ (*)
  begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
		default : y = i2;
	endcase
  end
  endmodule
  ```
- Running simulation using verilog and gtkwave
  
![comp_case_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/0add1e2b-c72e-473c-9768-a3727e892cd0)

- running synthesis using yosys

![comp_case_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/f5acf596-3a7e-44e4-88ad-0db944facdf7)

- here we see no inferred latch

**LAB_3 partial case assignment**
we look into how partial case assignments cause the formation of inferred latch.

**RTL code for partial _case_assign.v**
```bash
module partial_case_assign (input i0 , input i1 , input i2 , input [1:0] sel, output reg y , output reg x);
always @ (*)
begin
	case(sel)
		2'b00 : begin
			y = i0;
			x = i2;
			end
		2'b01 : y = i1;
		default : begin
		           x = i1;
			   y = i2;
			  end
	endcase
end
endmodule
```
- Running simulation using iverilog and gtkwave
  
![partial_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7d10e560-84ff-457f-b60f-78c9b790ed45)

- Synthesis using yosys

![partial_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/603f722c-5d3f-4773-9559-7e8357e588a1)

- Its is noticed that we have a latch in the design of the hardware even when we didn't had one in RTL file. This is due to the partial case assignment.

**LAB_4 the bad Case**
Under this, we look into the case of a bad case, which has simulation synthesis mismatch due to 
the improper assignment for case 1'b1?. This leads to formation of inferred latches.

**RTL code for bad_case.v**
```bash
module bad_case (input i0 , input i1, input i2, input i3 , input [1:0] sel, output reg y);
always @(*)
begin
	case(sel)
		2'b00: y = i0;
		2'b01: y = i1;
		2'b10: y = i2;
		2'b1?: y = i3;
		//2'b11: y = i3;
	endcase
end

endmodule￼
```
- Simulation using iverilog and gtkwave

![bad_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/afdafa38-0dc7-4f4c-825c-2c8cf3f630cb)

- Synthesis using yosys

![bad_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e10948cf-b39b-469b-8421-67b09383f1d8)

- Running GLS using iverilog and gtkwave fromnetlist obtained under synthesis

![bad_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/912e7847-9f11-4d9c-9c4b-88d3fc482661)

- We can see the mismatching under GLS and RTL simulation. This is due to improper assignment and formation of latches which weren't a part of the intended logic design.
</details>

<details>
<summary> for loop and for generate </summary>
	
**For Loop**

- For look is used in always block
- It is used for excecuting expressions alone

**Generate For loop**

- Generate for loop is used for instantaing hardware
- It should be used only outside always block

For loop can be used to generate larger circuits like 256:1 multiplexer or 1-256 demultiplexer 
where the coding style of smaller mux is not feesible and can have human errors since we would 
need to include huge number of combinations.

FOR Generate can be used to instantiate any number of sub modules with in a top module. For 
example, if we need a 32 bit ripple carry adder, instead of instantiating 32 full adders, we can 
write a generate for loop and connect the full adders appropriately.
</details>

<details>
<summary> LAB on **for** and **for generate** </summary>

**LAB_1 mux using Generate**

- Under this, we implement a mux using for loop.
- Advantage of this method over if-case method is that we don't have to write multiple lines.
- For a 64 input mux, using if-case we need over 64 lines of code, whereas the same can be done under 5-6 lines using for loop.
**RTL code for mux_generate.v**
```bash
module mux_generate (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;
always @ (*)
begin
for(k = 0; k < 4; k=k+1) begin
	if(k == sel)
		y = i_int[k];
end
end
endmodule
```
- Running RTL simulation using and gtkwave
  
![mux_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/293c7834-6548-4fab-85da-b69d35e4c27d)

- Synthesis using yosys

![mux_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/7a53ad94-78d3-4e2c-b6ac-b3da3c5911d9)

- Running GLS using iverilog and gtkwave after generationg netlist using yosys

![mux_gtk_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/6f7be624-ddb8-4390-b62a-b2ee456bb96c)

- It is observed that both the RTL simulation and GLS have same output waveform. Thus we have
the correct design.

**LAB_2 demux using generate**
Under this, We follow up with the implementation of demux

**RTL code for demux_generate.v**
```bash
module demux_generate (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
for(k = 0; k < 8; k++) begin
	if(k == sel)
		y_int[k] = i;
end
end
endmodule
```
- Simulation using iverilog and gtkwave

![demux_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/50e22695-0ecb-44b8-9443-312c7360f186)

- Syntheis using yosys

![demux_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/78035c6b-cb9f-458f-961e-fcc9888235e9)

- Running GLS using iverilog and gtkwave after generating netlist on yosys

![demux_gtk_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e7b7c88b-b292-4187-87a4-b4895d1e91d2)

- We see that both the waveforms for GLS and RTL simulation are the same. Thus we have the correct logic implementataion for demux.

**LAB_3 ripple carry adder**

- Under this, we look into implementation of an 8 bit ripple carry adder.
- In this we need 8 single bit adders, that is instantiate single bit full adder 8 times. We implement generate for for making this into a simple and shorter code.

**RTL code for rca.v**
```bash
module rca (input [7:0] num1 , input [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0]int_co;

genvar i;
generate
	for (i = 1 ; i < 8; i=i+1) begin
		fa u_fa_1 (.a(num1[i]),.b(num2[i]),.c(int_co[i-1]),.co(int_co[i]),.sum(int_sum[i]));
	end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));


assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```
- RTL simulation using iverilog and gtkwave

![rca_gtk](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/93f3a0b1-5aec-4ee1-be64-db5c2ec9e942)

- synthesis using yosys and rca grahical representaion

![rca_synth](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/866aa5fa-219d-4303-ba67-8b2670282f7c)

- show fa

![fa](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/2df36130-28a8-411c-aa57-9f1a3b30e03e)

- Running GLS using iverilog and gtkwave after generating a netlist using yosys

![rca_post](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/077fd1ee-0f8d-44c2-b18a-b012cb715b24)


- We see the same simulation and GLS waveform, thus the ripple carry adder logic is correct and
has been correctly synthesizer. The advantage of using generate for is that we have to
instantiate once and the code multiple copies, ie multiple instances as defined.
</details>
