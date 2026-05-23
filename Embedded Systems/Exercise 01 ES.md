Question 1

a) What is an embedded system? 
Embedded system is a system integrated into another technical system (embedding system).

Purpose: influence the embedding system such that it behaves in the desired way. 

b) What is the source of requirements for an embedded system? 
Requirements of an embedded system are derived from the requirements of the embedding system. 

Example with the motor: in order to control a motor to design a controller you have to know the requirements of the motor.

c) There are 2 categories of embedded systems: 
1. What are these categories? 
2. What are their characteristics? 
3. what kind of hardware is typically used for these categories? 
4. Which programming languages are the most dominant in these categories? 
5. Name at least one example for each category.

| 1.  | product automation<br>(motor controller;)                                        | production automation<br>(PLC in manufacturing programmable logic controller)                                                              |
| --- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| 2.  | many identical units (cost per unit is critical; design should be user-friendly) | often are identical unit<br>(cost is less critical; "customers" are close to being experts, because they're trained to use the controller) |
| 3.  | Microcontrollers, Field Programmable Arrays                                      | Programmable logic controllers, PCs                                                                                                        |
| 4.  | C/C++                                                                            | Instruction list, Sequential Function Chart, ST                                                                                            |
| 5.  | microvawe                                                                        | chemical plant controller                                                                                                                  |

d) What is a microcontroller?
1. Microprocessor. mandatory
2. Memory (RAM, permanent memory) mandatory
3. Digital I/O + other peripherals. (optional)

Task 2. 
In this task we refer to Atmel ATmega16 microcontroller. Assume 8 buttons are connected to PORTA and GND. Also assume, that 8 LEDs are connected to PORTB and Vcc such taht can be lit.

a) What are the register that control these ports? 
Data Direction register (DDRA, DDRB) Input/Output.
PortA, PortB 