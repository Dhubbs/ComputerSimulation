# ComputerSimulation
For this project DLS software was used to create a simulated computer. This is not a normal architecture; it was developed by me as I attempted to answer problems as they arose. Because conditionals have not been added, it is not technically turing complete at this time. The components for jumps have been added, but they have not yet been implemented in code. 
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Screen%20Shot%202022-02-09%20at%207.25.25%20PM.png)

## Memory 
To begin, we'll discuss how this computer's memory is built. The primary memory units are constructed to handle 16 8-bit numbers, and all data is saved in 8-bit format. It is constructed as a single module and is controlled by flags for reading and writing.

We will start from the bottom and work up showing each component along the way.
### 1 8 bit value
There are two inputs on this module. The first input is an 8-bit integer that represents the value to be stored, while the second is a clock signal. On the rising edge of the clock, data is overwritten. The output is an 8-bit value of whatever is being saved, and it outputs continuously. This implies that by enabling the clock and disabling it, values may be rewritten and saved.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.18%20PM.png)


### 4 8 bit values
This module extends the 1 8 bit values module by combining four of them and adds additional circutry to make the storage easier to utilise. The inputs consist of an 8-bit value that may be saved. To pick the unit to interact with, a two-bit selection value is used.   A 1 bit flag for writing causes the 8 bit value to be written to whichever module the 2 bit selection chooses. A 1 bit flag that enables reading from any unit picked with the selector. It is possible to allow both read and write at the same time. If the read flag is not set, the output is an 8-bit value will always be 0.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.10%20PM.png)


### 16 8 bit values
This module is made up of 4 4 8 bit value modules as well as various cicutry to make things easier. It has the same io as the 4 8-bit modules, however the selection is four bits, allowing all 16 storage locations to be utilised. This is the total amount of accessible memory that I have decided to utilise for this computer; but, by climbing one order higher, it may be expanded to hold 64 values.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.03%20PM.png)

## Periferals
The computer relies on numerous components in addition to memory. Because this is a small computer, these "extra" modules are limited. However, I opted to build these components to be extendable and simple to utilise for future projects. Except for the main bus, which is controlled by two 3 bit control signals, all data flowing through the computer utilises 8 bit values and typically 1 bit flags to regulate processes.

### Main Bus
To get started, let's speak about the main bus, which permits data to flow freely throughout the computer. This module is designed to accept 8 8-bit values as input and output 8 8-bit values, its primary job is to act as plumbing, matching any input to any output. The control signals are two three-bit values that indicate which input to read from and to which output to deliver the value. In the design above of the whole computer, I utilised a previous version (not shown below) that had five 8-bit inputs and five outputs.
input 1 = Direct value load
input 2 = Memory Output
input 3 = Alu Output
input 4 = Registar A Output
input 5 = Registar B Output

Output 1 = Memory Load
Output 2 = Registar A
Output 4  = Registar B
Output 4 = Unused
Output 5 = Main Display

We can transport data between different memory positions by sending it across the bus by linking memory as both input and output.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Periferals/Screen%20Shot%202022-02-09%20at%207.26.47%20PM.png)

### Displays
I picked two seven segment displays to display values in a base 10 format for the dis on this computer. Because the screens can only display up to the value 99, and all data is 8 bits, and not all values can be conveyed. The input to this module is an 8-bit value, and the output is a base-10 value. This was a fun module to make since I used a rom module with 256 readable addresses and built a lookup table with the first 99 places programmed to output the necessary control signals to switch on the separate segments. Because the rom module is written in raw hex, I created a python script to produce the lookup table of codes, which saved me a lot of time
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Periferals/Screen%20Shot%202022-02-09%20at%207.28.13%20PM.png)
here is the hex lookup table
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Periferals/Screen%20Shot%202022-02-09%20at%207.28.25%20PM.png)

### ALU
Instead of focusing on establishing an in-depth ALU for this project, I focused my efforts on memory systems and overall system development. I chose to construct an ALU that just supports addition, but adding subtraction should be simple in the next version. The inputs are two 8-bit numbers and a carry-in flag, and the calculation is performed using eight 1-bit full adders. The output is one 8-bit value and a carry-out flag. I inserted 8bit registars before the inputs as part of the overall system architecture to allow computations to be conducted between cycles.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Periferals/Screen%20Shot%202022-02-09%20at%207.29.28%20PM.png)
