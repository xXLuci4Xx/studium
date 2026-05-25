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
In this task we refer to Atmel ATmega16 microcontroller. Assume 8 buttons are connected to PORTA and GND. Also assume, that 8 LEDs are connected to PORTB and Vcc such that can be lit.

a) What are the register that control these ports? 
Data Direction register (DDRA, DDRB) Input/Output.
PortA with pullup resistor (for input), PortB output value (for output) 

b) How should these registers be initialized? 
1. Since PORTA represents an input, DDRA should be initialized as DDRA = 00000000 or $(00)_{16}$ (that setting lead's to choose pull-up resistor inside the atmega16 chip), whereas PORTB represents the output and since that DDRB should be initialized as DDRB = 11111111 or $(FF)_{16}$. 
2. Now PORTA obviously should be connected to the pull-up registers to activate the button, so PORTA = 11111111 = $(FF)_{16}$. Other choice would be high-z mode, but that would make no sense. For PORTB = (111111111) = $(FF)_{16}$ to make sure that initially LEDs are off, so when PORTB is 0 —  LEDs are turned on/ 1 — turned off. 

c) Write a loop that allows to control the LEDs via the buttons: 
1. On a 1-to-1 basis (pushing button 4 causes LED 4 to be lit)
2. Priority encoder: show the binary coding for the number of the highest button pushed.

Solution 1: 

```C
while(1) {
	for(i = 0; i <= 7; i++) {
		PORTB = PORTA
	}
}
``` 
So the direct assignment possible. 

Solution 2: 

```C
while(1) {
	int i; // shouldn't we leave here byte instead? 
	for(i = 7; i>=0; i--) {
		if(~PINA & (1<<i)) {
			PORTB = ~i;
			break;
		}
	}
}
```
7   6   5 4  3  2 1  0
[] {x} [] [] {x} [] [] []
So this represents buttons number 6 and 3 being pressed. 

We want PINA 10110111 —> PORTB 11111001 since the highest pressed button is 6. 

Therefore values on the PINA will be 10110111, hereby we need to invert PINA with ~ to be able to bit-wise  compare it to the left-shifted one for the amount of i. This method selects the biggest button pressed. Afterwards we just assign to PORTB the inverted with ~ version of the i to get the binary representation of the number of the pressed button, because the inversion of i is the resulting PORTB value we wish to achieve. 

d) What is bouncing? Implement a debouncing method.

The bouncing is the signal oscillation/fluctuation during a signal change before the signal reaches a steady state. 

We can use lowpass filter as a hardware solution. 
We count cycles after last change occurred and change recognized input level after a certain amount. 

Task 3
a) Choose interrupts or polling for the following scenarios and explain your choice.
1. The "change imput"-button on a monitor.
	 Interrupt, because of rare changes.
2. The wireless-receiver of a garage-opener.
	 Interrupt. because of signal changes. But polling may be preferable, since security reasons imply noice-robustness.
3. The keyboard on a standard desktop.
	 Polling, because of many signal changes, keyboard also uses buffering: so it sends filled buffer every n milisecs not to delay the program. 
4. The temperature-sensor of a weather-station.
	Polling, because we need a continuous measurement. 

b) When is an ISR (Interrupt Service Routine) called and how is it done? 

When global interrupt enable bit (GIEB), specific interrupt enable bit, Interrupt flag = 1. So all those 3 bits should be set to 1. 

How: 
	1) PC is stored Program counter should be stored,
	2) GIEB to 0,
	3) Set PC Look-Up-Table (Vector Table),
	4) Set PC to ISR,
	5) Context ISR,
	6) Execute ISR,
	7) Restore Context,
	8) Restore PC <-> set GIEB to 1