# omni-serial
UART for PDP-9 Omnibus computers based on ATF1508AS CPLD

This project is a single-chip UART for a PDP-8 Omnibus machine (PDP-8/e, etc).

It uses an ATF1508AS CPLD. No other glue-logic or bus-interface ICs are required.  Some supporting components (such as an external XTAL, dipswitches, LEDs and connectors) are required.

The PCB design and initial CPLD code (for the UART side) were developed by Alan Hightower.

The CPLD code for the Omnibus side was developed by Malcolm Macleod.

Further improvements to the code by others are very welcome.

Current status:

30-SEP-2016: Board is working, but testing so far has been minimal. It works fine as the Console interface when booting OS/8 from another device. It also works fine as the second SLU (at Device Code 40/41) to boot OS/8 from a RPi running Kyle Owen's SerialDisk server. It runs at a fixed baud rate of 115,200. To-Do items: (1) implement switch-selectable baud rates of 110, 300, 1200, 9600, 38400, 115200 and 230400. (2) Simplify the INT_EN status LED (remove the 4-bit timer connected to it). (3) Have INT_EN default to ON (for compatibility with KL8-E design). (4) Look to reduce the macrocell count if possible. (5) Allocate outputs to unused pins, to avoid them being spuriously driven by flip-flops that were not intended to be externally exposed.

