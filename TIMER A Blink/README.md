# TIMER A Blink

Timers can be set up in different ways for a wide variety of functions. Timers can be broken into mainly two components. The counter and the capture/compare register. The counter just takes a selected clock signal (MCLK, SMCLK, ACLK) and counts each pulse. The total count is stored in the TAxR or TBxR registers. There are four modes in which the timer can be set which are stop, up, continuous, and up/down. Up mode has the counter count up to a certain value before reseting, continuous mode has the counter go up as high as possible before an overflow occurs, Up/down mode has the counter count up to a value and then back to zero, and Stop just halts the register. Also, before the clock is sent to the counter, you have the option to divide the clock using the internal divider, lowering the frequency. 

In relation to the lab, 
