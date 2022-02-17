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
