# Peak-Current-Halfbridge
An FPGA implementation of a digital peak-current controlled half bridge in Verilog.

Verilog module for driving a half-bridge (HB) conveter topology in digital current mode control.				
																												
Theory of operation: This module is very similar to a duty cycle mode controlled HB.							
In a nutshell, the high side FET is turned on. The inductor current rises, and a comparator						
on the board itself flips when the inductor current reaches a preset reference. This is accomplished			
by using high-side current sense resistor and some isolation circuitry. When the comparator (cmp) flips high,	
a flag is set. The high side is then turned off, a counter clocks the dead time, and the low side FET 			
is turned on for the remainder of the switching period. 														
																												
Inputs/Outputs:																									
clk: FPGA system clock input. 																					
cmp: The high-side current sense comparator input.																
DT: Dead time in sysclk ticks.																					
MaxCount: the length of a switching period in sysclk ticks.														
High: Hide side MOSFET gate drive signal.																		
Low: Low side MOSFET gate drive signal.	