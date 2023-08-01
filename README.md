# IIITB_ASIC_course
[Day 0](#day-0)

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
 <summary> magic </summary>


 I installed magic using the following commands:
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

# After reboot
docker run hello-world

 ```

Below is the screenshot showing sucessful launch:
 ![OpenLane](https://github.com/SahilSira/IIITB_ASIC_course/assets/140998855/e35808de-44e9-41c5-86d2-6e29f90b6623)


</details>
