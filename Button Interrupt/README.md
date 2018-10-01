# Button Interrupt

Getting the a button to blink using an interrupt instead polling is really not too different. The button and the port connected to the LED have to set as I/O (PxSEL), the button has to set as an input and the LED as an output (PxDIR), and the pull-up resistor connected to the button has to be enabled (PxIE / PxOUT = 1). The big difference is the set of code below. 

```c
__bis_SR_register(CPUOFF + GIE)

#pragma vector=PORT1_VECTOR
__interrupt void Port_1(void)
{
  // Code for interrupt routine here
}
```
The first line of code puts the microcontroller into low-power mode, turning off the CPU. While the CPU is idle, it waits until an interrupt is flagged (button is pressed). Once the interrupt is flagged, everything is stopped and pushed to the stack, and the interrupt routine begins, which is what the rest of the code shown above defines. Once the interrupt routine is over, the previous data is removed from the CPU and the CPU continues as it was before. When using any interrupt, it is important to enable the interrupt for whatever the stimulus is, whether it is a port, timer value, or etc.

  PxIE : Enables interrupt for port pin
  PxIES : Determines if interrupt is based on rising or falling edge
  CCIE: Enable interrupt for CCR value
  GIE: Global interrupt enable

