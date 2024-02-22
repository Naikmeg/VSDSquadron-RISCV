# Research Internship on VSDSquadron Mini RISC-V Development Board

The internship is based on RISC-V Development Board(VSDSquadron Mini),which is a flagship product of VLSI System Design.This is a 4-week internship program on RISC-V.
The internship is categorized into 3 levels: **Beginner  Intermediate    Advanced** <br>
I have opted for the Beginner course, where I would be learning about RTL development.<br>
Below is the infromation about the VSDsquadron Mini board. For more information visit the official [website](https://www.vlsisystemdesign.com/vsdsquadronmini/)
<details>
  <summary><b>VSDSquadron Mini Board</b></summary>
  <br>
  <p align="center">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/878bfd69-dc20-4b37-933a-6ca385541c28">
  </p>
  <hr>
    <h3><b>Specifications</b></h3>
    <br>
<p align="center">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/d880e374-302d-4250-9d8a-f208a360af78">
  </p>  
</details>
This repostory will be used for weekly updates of the tasks assigned during the Internship.

<details>
  <summary><H4>Task 1</H4></summary>

  ### Meeting was conducted on 16th of February 2024 at 6PM IST
  <hr>
<b>Tasks Assigned:</b>

  * Installation of git
  * Installation of Yosys
  * Installation of iverilog
  * Installation of gtkwave

<hr>

<b>1. Git Installation </b>

Code:<br>
`sudo apt install git-all`<br>

<p align="left">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/73e1a10e-4b45-446f-bd47-1ada5c274efe">
  </p> 

  <b>2. Yosys Installation </b>

Code:<br>
```
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install
```
<p align="left">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/cec94b78-5a03-4342-a973-56462845812b">
  </p> 

<b>3. Iverilog Installation </b>

Code:<br>
`sudo apt-get install iverilog`<br>

<p align="left">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/cea20a5c-f6f1-4f35-9fc3-7d610417f826">
  </p> 

<b>4. Gtkwave Installation </b>

Code:<br>
```
sudo apt update
sudo apt install gtkwave
```

<p align="left">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/5815289b-969a-40d2-8b1f-d8e53eaaeb8b">
  </p> 

</details>
<details>
  <summary><H4>Task 2</H4></summary>

  ### Meeting was conducted on 20th of February 2024 at 6PM IST
  <hr>
<b>Tasks Assigned:</b>
To create a block representation to identify :

* Input Port
* Input Waveform
* Output Port
* Output Waveform
<hr>
<b><p align="center">
  Universal Asynchronous Receiver Transmitter Protocol based hardware transmitter
  </p> </b>
<p align="center">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/4bc5b24f-cb64-4d57-b1dd-bf089403cbd8">
  </p> 

  ### Protocol Overview
<p align="left">
  <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/02dc572d-7191-40f1-9795-3abe2e7416c3">
  </p> 
<b>The Idle state refers to that the transmission has not begun.It is represented through a high pulse.The start bit is represented through a 0 pulse and the data is represented through d0 to d7.The following steps are used to transmit the data and receive it.<br></b>
1.Wait until incoming signal becomes 0 (start bit), then start the sampling tick counter<br>
2.When tick counter reaches 7 (middle of start bit), clear tick counter and restart<br>
3.When counter reaches 15 (middle of first data bit), shift bit value into register & restart tick counter<br>
4. Repeat step 3 (N-1) more times to retrieve the remaining data bits<br>











