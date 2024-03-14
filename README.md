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
<br><br>
<details>
<summary>Task 1</summary>
  
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
  <summary>Task 2</summary>

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
  </p> </b><br>
  <b>Introduction</b> 
  
UART transmitter is used here to transmit the serial data to receiver module of other UART device.We input the data in parallel form but it is sended out serially.Transmitter module converts the parallel data into serial bit stream. 

UART transmits asynchronously which means there is no need to transmit clock signal with the transmitted data.
Instead of clock, the transmitter transmit data with some special bits to synchronize the sending and receiving inputs.
These bits define the beginning and end of the data packet so the receiving UART knows when to start and stop reading the bits.
These special bits are <b>(START,DATA,PARITY,STOP)</b> bits.
<p align="center">
   <img src="https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/f1260241-cae8-4155-8f8e-646bd60c2cf9">
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
</details>
<details>
<summary>Task 3</summary>

  ### Meeting was conducted on 22nd of February 2024 at 6PM IST
  <hr>
<b>Tasks Assigned:</b>

* Simulation of code and testbench file
* Generate the waveform
<hr>
<b>To generate the code and testbench file:</b>
  
```
gedit uart_tx.v
gedit uart_tx_tb.v
```
<b>To simulate iverilog</b>
```
iverilog -o uart_wav uart_tx .v uart_tx_tb.v
```
<b>To generate waveform</b>
```
vvp uart_wav
gtkwave dump.vcd
```
![code_uart](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/af4cd40d-7539-457a-a40f-b838c211f4c1)

<b>Waveform</b>
![Screenshot from 2024-03-12 18-21-37](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/02a3b44a-ce7f-49b3-a070-33909993ff81)

</details>

<details>
<summary>Task 4</summary>

  ### Meeting was conducted on 1st of March 2024 at 6PM IST
  <hr>
<b>Tasks Assigned:</b>

* Synthesis using Yosys
* Verification of netlist using iverilog and gtkwave
<hr>
<h3><b>To generate the synthesis file:</b></h3>
<b>Yosys</b>

```
git clone sky130RTLDesignAndSynthesisWorkshop
yosys
```
<b>Synthesiszing the netlist file</b>
```
read_liberty -lib../sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
read_verilog uart.v
synth -top uart
abc -liberty../sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
show
```

<b>Write and view the netlist file</b>
```
write_verilog -noattr netlist.v
!gedit netlist.v
```
<h3><b>Verification using iverilog and gtkwave:</b></h3>

<b>iverilog</b>

```
iverilog ../sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/primitives.v ../sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/sky130_fd_sc_hd.v netlist.v tb_uart.v
./a.out
```
<b> gtkwave</b>
```
gtkwave dump.vcd
```

<b>Code</b><br><br>
Yosys:
![Screenshot from 2024-03-12 18-41-10](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/14365326-78ca-4262-95bd-7ffe6f864ca6)

Synthesis:
![Screenshot from 2024-03-12 18-41-30](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/59b2d105-d9d0-485b-8e3a-723a92359d71)

Show Command:
![Screenshot from 2024-03-12 18-35-34](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/81558ec3-79e6-43ad-8f58-c1c9144c17c3)

iverilog and gtkwave:
![Screenshot from 2024-03-12 18-42-23](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/c5a93dc5-2fb4-4271-9aec-ecb4909c6289)

<b>Waveform Verification</b><br><br>
uart_tx.v :
![Screenshot from 2024-03-12 18-21-37](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/99487d9e-b91b-4428-bb76-a721988298f4)

netlist.v : 
![Screenshot from 2024-03-12 18-23-33](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/89faf6be-9473-4b81-a59e-710c0975e986)

<b><h3>Since both the waveforms match the synthesis is verified.</h3></b>
</details>




<details>
<summary>Task 5</summary>

  ### Meeting was conducted on 7th of March 2024 at 6PM IST
   <hr>
<b>Tasks Assigned:</b>
Functional verification using verilog netlist and tesbench provided in the reference github repository.
<hr>
<h3><b>To simulate and generate waveform:</b></h3>
<b>iverilog</b> 

```
git clone iiitb_uarttx
iverilog iiitb_uart_tx.v iiitb_uart_tx_tb.v
./a.out
```
<b>gtkwave</b> 

```
gtkwave dump.vcd
```
![Screenshot from 2024-03-13 18-41-17](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/4a4dcf93-1c5e-4fe1-88d7-6e51cf220090)

![Screenshot from 2024-03-13 18-34-10](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/5547557c-7377-4e84-a757-0904583dbe52)



<h3><b>To generate the synthesis file:</b></h3>
<b>Yosys</b>

```
yosys
```
<b>Synthesiszing the netlist file</b>
```
read_liberty -lib lib/sky130_fd_sc_hd_tt_025C_1v80.libread_verilog iiitb_uarttx.v
read_verilog uart.v
synth-top UART_TX
abc liberty lib/sky130_fd_sc_hd_tt_025C_1v80.lib
show
```

<b>Write and view the netlist file</b>
```
write_verilog -noattr netlist.v
!gedit netlist.v
exit
```
<h3><b>Verification using iverilog and gtkwave:</b></h3>

<b>iverilog</b>

```
iverilog primitives.v sky130_fd_sc_hd.v netlist.v iiitb_uarttx_tb.v iiitb_uarttx_tb.v
./a.out
```
<b> gtkwave</b>
```
gtkwave dump.vcd
```
<br>
<b>Code</b><br><br>
Yosys:<br>

![Screenshot from 2024-03-13 18-41-26](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/34aae172-ddf6-4667-b1b9-f3883ad939de)

Synthesis:<br>
![Screenshot from 2024-03-13 18-41-41](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/a997a6ba-6d7d-48cd-90e1-d0402270bfcc)

Show Command:

![Screenshot from 2024-03-13 18-38-36](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/07caeb4f-487f-4309-aca2-9b2bebb30d3e)

iverilog and gtkwave:

![Screenshot from 2024-03-13 18-42-54](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/178670f4-a2d2-4587-b63f-7e0bec3cd8e2)


<b>Waveform Verification</b><br><br>
uart_tx.v :

![Screenshot from 2024-03-13 18-34-10](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/e75903cf-e2cb-4eda-b934-3ca14c7059c6)

netlist.v :

![Screenshot from 2024-03-13 18-40-46](https://github.com/Naikmeg/VSDSquadron-RISCV/assets/72155259/a28e197f-8d48-4458-b282-e9430d88b610)

<b><h3>Since both the waveforms match the synthesis is verified.</h3></b>
</details>

<details>
  <summary><b>References</b></summary>

  <u>Course</u> -<br> 
  [VSD](https://www.vlsisystemdesign.com/vsdsquadronmini/](https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/)https://www.udemy.com/course/vsd-a-complete-guide-to-install-open-source-eda-tools/) <br>
  <u>Reference repositories</u> - <br>
  [vsdflow](https://github.com/kunalg123/vsdflow.git) <br>
  [sky130RTLDesignAndSynthesisWorkshop](https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git) <br>
  [uarttx](https://github.com/jayshah1x/iiitb_uarttx.git) <br>
</details>

