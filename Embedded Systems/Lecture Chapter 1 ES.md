Definitions: 
- Data Direction Register (DDR)
	  - Read and write 
	  - specifies for each bit of the corresponding port whether it's an input (0) or an output (1)
- Port Register (PORT):
	  - read/write 
	  - specifies for the output pins whether the output value is high or low
	  - ATmega16: also used for controlling pull-up resistors for input pins
- Port Input Register (PIN):
	  - read only (writing has no effect or unintuitive semantics)
	  - contains the current value (high or low) of all pins (input and output)
	  - usual purpose: reading values of input pins

![[Lecture1Chapter1Example1LEDControlES.png]]![[Lecture1Chapter1Example2LEDControlES.png]]
Data Direction Register ensures that physical data flow goes to a certain point whereas PORT specifies the output pin whether the value is high, low or high-impedance. 
In both examples DDR is set as an output. 

![[Media/Lecture1Chapter1Example3ReadingAButtonES.png]]
Here we create a tri-state. 
*Important thing to remember*: voltage is the logic level! To read a logic level we're reading a voltage level.
![[Lecture1Chapter1Example2ReadingAButtonES.png]]
Since the button is not pressed, we will read 1 as the value on the pin. Here is pull-up resistor used.
![[Lecture1Chapter1Example3ReadingAButtonES 1.png]]
Pin is closed, current is moving.

# Digital I/O Summary
![[Lecture1Chapter1DigitalIOSummary.png]]