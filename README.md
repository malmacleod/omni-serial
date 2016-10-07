# omni-serial

Single bi-directional serial interface for PDP-8 Omnibus computers based on ATF1508AS CPLD

It uses only one IC (the Atmel ATF1508AS CPLD). No other glue-logic or bus-interface ICs are required.  Some supporting components (such as an external 1.8432 MHz oscillator, dipswitches, LEDs and connectors) are required.

It emulates a DEC KL8-E (M8650) with a couple of enhancements, such as selectable baud rate.

The PCB design and initial CPLD code (for the UART side) were developed by Alan Hightower.

The CPLD code for the Omnibus interface, and enhancements to the UART code, were added by Malcolm Macleod.

The PCB design was done in Eagle, and the CPLD code was developed using WinCupl.

Further improvements to the code by others are very welcome.

##Current status:

03-OCT-2016 (Version 01.01): MAIN.PLD updated as follows:
* Added selectable baud rates (110, 300, 600, 1200, 9600, 38400, 115200 and 230400)
* Added selectable Device Code pairings (7 settings eg 03/04, 40/41, etc) 
* Modified RX and TX state machines to work with only one stop bit
* Tuned RX and TX state machines
* Interrupt enable now defaults to ON (same behaviour as real KL8-E)
* Other minor changes as described in the MAIN.PLD file

The board now:
* Successfully boots SerialDisk at 230,400 baud (at Device Code 40/41)
* Works fine as the System Console at 9,600 baud (at Device Code 03/04)
* Can successfully echo-back an ASCII text file that is dumped to it at 230,400 baud via TeraTerm with no handshaking (with appropriate echo-test code running on the PDP-8/e).
* Seems to implement interrupt functionality correctly (this has been verified by single-stepping through an interrupt test routine running on the PDP-8/e).

##Revision History
30-SEP-2016 (Version 01.00): Board is working, but testing so far has been minimal. It works fine as the Console interface when booting OS/8 from another device. It also works fine as the second SLU (at Device Code 40/41) to boot OS/8 from a RPi running Kyle Owen's SerialDisk server. It runs at a fixed baud rate of 115,200. To-Do items: (1) implement switch-selectable baud rates of 110, 300, 1200, 9600, 38400, 115200 and 230400. (2) Simplify the INT_EN status LED (remove the 4-bit timer connected to it). (3) Have INT_EN default to ON (for compatibility with KL8-E design). (4) Look to reduce the macrocell count if possible. (5) Allocate outputs to unused pins, to avoid them being spuriously driven by flip-flops that were not intended to be externally exposed.
