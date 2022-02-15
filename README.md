# ComputerSimulation
Simulated Computer made in a software called DLS. this does not follow a typical architecture and was built by me trying my best to solve issues as I saw them. At this point it is not technically turing complete as conditionals have not been implemented. The components for jumps has been put in however not implemented in code 
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Screen%20Shot%202022-02-09%20at%207.25.25%20PM.png)

## Memory 
to start with we will talk about how memory is designed in this computer. All data is stored as 8 bits and the main memory units is built to hold 16 8 bit number. It is built as one module and is driven off flags for reading and writing.

We will start from the bottom and work up showing each component along the way.
### 1 8 bit value
this module has 2 inputs the first is a 8bit number repersenting what value is to be stored and the second input is a clock signal. Data is rewritten on a rising edge of the clock. The output is a 8 bit value of what ever is being stored and is constantly outputting. This means that values can be rewritten by enabling the clock and stored by disabling the clock
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.18%20PM.png)


### 4 8 bit values
This module builds on the 1 8 bit values module and combines 4 of them together while adding additional circutry to simplify the use of the storage. 
The inputs are an 8 bit value that can be stored. A 2 bit selection value to choose which unit to interact with. The clock. A 1 bit flag for writing that makes the 8 bit value be written to whatever is selected from the 2 bit selector. A 1 bit flag to read from any unit that is selected with the selector. Both read and write can be enabled. The output is a 8 bit value that and will be 0 if the read flag is not set
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.10%20PM.png)


### 16 8 bit values
This module is composed of 4 4 8 bit value modules and also incorporates other cicutry to simplify things. It has the same io as the 4 8 bit modules except for the fact that the selector is 4 bits to allow all 16 spots to be used. This is as total amount of addressable memory that I have chosen to use for this computer however it could be expanded further and could store 64 values by moving one level higher.
![alt text](https://github.com/Dhubbs/ComputerSimulation/blob/main/Memory/Screen%20Shot%202022-02-09%20at%207.27.03%20PM.png)
