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
simar-thethi@simar-thethi-Inspiron-3542:~/vsd/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files$ multiple_modules.v
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
![vsd day_2 multiple module yosys](https://github.com/simarthethi/iiitb-asic/assets/140998783/f689253a-3682-4080-b4aa-06ac8d1436c7)
![vsd day_2 reading verilog file](https://github.com/simarthethi/iiitb-asic/assets/140998783/af199fa9-8b89-413c-8619-191c19e687b1)
![vsd day_2 generate netlist m_m](https://github.com/simarthethi/iiitb-asic/assets/140998783/ce6f9abf-f5e4-493f-ad6d-503905bd9300)

- we hit show and expect to attain a similar schematic we had drew
  ![vsd day_2 show graphical rep of m_m](https://github.com/simarthethi/iiitb-asic/assets/140998783/31a1f607-589b-44f1-b463-b5b793512e67)


- We get the image of the top module.
- We don't get to see the and and or gates. We see the modules u1 and u2, which are the instances of the gates.
- **This type of design is called an heirarchial design.**
- We generate the netlist file for the design.
```bash
write_verilog -noattr multiple_modules_hier.v
!gvim multiple_modules_hier.v  
```
![gvim of m_ hiererchial](https://github.com/simarthethi/iiitb-asic/assets/140998783/017232f1-274d-4a29-b288-aafd55ab7a3c)
![vsd day_2 gvim m_m hiererchial pt2](https://github.com/simarthethi/iiitb-asic/assets/140998783/aff0388c-a5d1-4d54-a903-243277e659fc)

- In the netlist generated, it is observed that the hierarchy is maintained. The top module has instances of sub moduke 1 and 2, and the two modules are seperately defined implementing the and and or gates.
- It is to be more, since this is CMOS technology, we implement the gates using a nand gate with inverted inputs for or gate and nor gate with inverted inputs for and gate.

Now we will look into flat design techcnique.
```bash
write_verilog -noattr multiple_modules_flat.v
!gvim multiple_modules_flat.v
```
![vsd day_2 gvim m_m flattop synthesis](https://github.com/simarthethi/iiitb-asic/assets/140998783/4f3fb545-0eb5-4a0b-ac0d-a9d595935eaf)
![flattop synthesis pt2](https://github.com/simarthethi/iiitb-asic/assets/140998783/7700a0f5-c504-4388-94b8-9f621a23028a)

- In the new netlist, we don't see any instances of submodules such as u1 and u2.
- We get direct instances of and and or gates under the flat design.
- This type of design is known as flat desigin techniques.

```bash
flatten
show multiple_modules
```
![vsd day_2 show multiple module flat](https://github.com/simarthethi/iiitb-asic/assets/140998783/75a2d5e4-4bce-4b08-adcb-d3e6037e3f76)
We saw how to synthesis the top module, now we will look into synthesis of submodules.
![vsd say_2 show sub_module 1](https://github.com/simarthethi/iiitb-asic/assets/140998783/e7a8c22e-b586-47e0-8e14-e18bf1977fa9)
- We only see submodule 1, we don't get to see the multiple module or submodule 2.

</details>
<details>
<summary> Various Flop coding styles and optimizations </summary>
Under this section, we go through all the various types of flops available and how to design and 
code them efficiently. All the required files are presen in the folder verilog_files.
To understand the need of flops, we refer the example of a simple circuit with delays as 2ns for 
and gate and 1ns for or gate.
 
![Screenshot from 2023-08-16 01-14-56](https://github.com/simarthethi/iiitb-asic/assets/140998783/823b6384-2b96-4bf6-9f9e-29960f572b73)


- Considering the input goes from 0 to 1 for a and b and simultaneously, 1 to 0 for c.
- Ideally for the transition from (001) to (110), the output should have been a constant at 1,
but because of the delay, we get outout as 0 for a brief period of 2ns.
- This is called a glitch.
![Screenshot from 2023-08-16 01-17-36](https://github.com/simarthethi/iiitb-asic/assets/140998783/32a7f827-b33c-4083-9ae7-ed5ddd611cba)

- More the number of combinational circuits, more number of glitches appear, giving a glitchy output.
- To avoid this, we need an element to store the value. Comes the flops into picture.
- We use a D flipflop. They are a storage element. They are placed between combinational circuits and changes value only at clock edge.
![Screenshot from 2023-08-16 01-19-10](https://github.com/simarthethi/iiitb-asic/assets/140998783/6f21888e-78ba-4fb3-a203-feb739b160ac)

- We need to initailise the flops, else the combinational circuits gives a garbage value. For this purpose we have reset and set pins. They can be asynchoronous and synchronous.

Types of flops

- Flops can be designed to be asynchronous or synchronous. It depends on whether the flop is sensitive to the reset and set parameters.
- Under asynchronous, the flop is sensitive to the reset or set, ie the design checks for them and the moment, reset is encountered, the output is pulled to 0 irrespective of the clock. For asynchronous set, the output is pulled to 1.
- The circuit design and timing diagram along with verilog code is displayed under the image below under column 1.
- Under the case of synchronous reset, the output is pulled to 0 at the next clock cycle. The design and timing diagram along the verilog code is shown under the column 2 of the image below.
- Sync reset can be understodd as the input is pulled to 0, thus output becomes 0 for next clock cycle.

![Screenshot from 2023-08-16 01-22-20](https://github.com/simarthethi/iiitb-asic/assets/140998783/770b73ce-325c-42c9-9e86-35995680fd99)

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
![vsd day_2 dff asyncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/63ca8084-3fb8-4bc6-a631-690fd92672d0)
![vsd day_2 gtkwave dff asyncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/00e0eca2-13f9-41eb-9ed1-7604185aa593)
- We can observe that the output q goes to 0 when the reset is encountered.
- Now we synthesis the design using yosys.

![vsd day_2yosys dff asyncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/e8c03f69-9d14-4824-bf0a-535504d8bec8)
![vsd day_2 reading dff ayncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/dd54d587-e4e1-4128-8a79-68370e35b5e2)

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
![vsd day_2 dff async set](https://github.com/simarthethi/iiitb-asic/assets/140998783/fc3ff189-8c67-478a-9ce3-fe12772e468c)
![gtkwave dff async set](https://github.com/simarthethi/iiitb-asic/assets/140998783/2f11ebf4-4daa-4b12-b53f-dd841782cf6d)

- We can observe that the output q goes to 1 as soon as we encounter the set irrespective of that clock. -Now we synthesis the design using yosys.
![vsd day_2 graphical dff  asynset](https://github.com/simarthethi/iiitb-asic/assets/140998783/d64f3b85-e656-4ac1-b58b-a48b000f0274)

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
![vsd day_2 syncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/988d2164-d386-4cbe-9de9-bf4178a15979)
![gtkwave dff syncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/541ecbfa-0abd-4983-bee4-27ba81108523)
- It is observed that the output q is set to 0 at the next clock pulse when the reset is encountered, thus it is the case of sync reset.
- Now we synthesis the design using yosys.
![vsd day_2 graphical repp dff syncres](https://github.com/simarthethi/iiitb-asic/assets/140998783/b473d2c0-9789-472f-bd15-7e33485c943f)

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
![Screenshot from 2023-08-16 02-08-26](https://github.com/simarthethi/iiitb-asic/assets/140998783/d9b3bdff-8374-463d-913c-88db7e39d59b)

- From these, we are able to infer that the logic requires the input to be multiplied with 2, and upon checking the output it is the input with 1'b0 padding.
- Thus the design for the logic needs no hardware to be mapped.
- We will confirm this using yosys.
![Screenshot from 2023-08-16 02-11-02](https://github.com/simarthethi/iiitb-asic/assets/140998783/c746b58e-d304-4586-a3a5-6b4b272ac42f)

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
![Screenshot from 2023-08-16 02-13-28](https://github.com/simarthethi/iiitb-asic/assets/140998783/df14eb46-1a54-4e03-a098-54ce543cf23e)

- Multiplcation with 9 can be seen as multiplication with 8 and plus 1.
- We know multiplication with 8 is equal to 3'b000 padding, and adding the same 3 bit number to the padded number comes of as concatanation of {a,a}.
- Thus there are no standard cell required for the design. We verify this using yosys.
![Screenshot from 2023-08-16 02-15-45](https://github.com/simarthethi/iiitb-asic/assets/140998783/20c612e7-3e59-4b14-9931-2d1810ede082)

- We see that there are no standard cells required.
- We see the concatanation operation done in the netlist.
</details>

