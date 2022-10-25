# Project Un-SBC

A personal project to reverse engineer a single-board computer built for a class lab project in 1997.

The board is like an oversized Arduino board, but much larger, built with discrete components, mounted to a perf board, and all connected with a rats nest of wire wrapping underneath.

I no longer have the original source code or schematics (partly because my laptop was stolen mid-project, but mostly because it was 25 years ago).

Goals:

* Figure out how the board works again without the schematics
* Backup the EPROMS before they start to fail
* Convert the machine code back to assembly
* Improve the serial, parallel, and dice interfaces
* Add new features?
* Document the process

## TOC

## Background

## Board Layout

Components

| ID | Qty | Markings | Description |
| -- | --- | -------- | ----------- |
| A | 1 | MC68HC000P12 | Motorola 68000 CPU |
| B | 2 | GM7628A-10 | SRAM, 2k x 8, 100ns, CMOS |
| C | 2 | M2732AFI 21V Fast | NMOS 32k 4k x 8 UV EPROM |
| D | 2 | 74LS32N | 8-input NAND gate |
| E | 1 | SN74AS138N | 3 to 8-line decoder/demultiplexer |
| F | 1 | *Unreadable* | Clock chip for serial |
| G | 1 | MC68681P | Dual async RX/TX (DUART) |
| H | 1 | 74S08PC | Quad 2-input NAND gate |
| I | 1 | ICL23CPE | +5V, powered Dual RS-232 RX/TX |
| J | 1 | 74LS373 | 3-state octal latches |
| K | 1 | 74LS164N | 8-bit serial to parallel shift register |
| L | 1 | 74LS10B1 | Triple 3-input NAND gate |
| M | 1 | SN7406J | Hex inverter buffers/drivers |
| N | 1 | SN74LS14N | Hex inverter, Schmitt |
| O | 1 | 127R OSC 10.000MHZ WE135 | Clock |
| P | 1 | 10X-1-331 B 9709 | Resistor pack |
| P | 1 | L10C472 710 | Resistor pack |
| Q | 1 | 97-11 IEE-ll7164R | 10-position LED display |
| R | 1 | No markings | 8-position DIP switch |
| S | 5 | 37V 45uF | Electrolytic cap, 45μF |
| T | 17 | 104Z | Ceramic cap, 0.1μF +80/-20% |
| U | 1 | *Unreadable* | Diode |
| V | 1 | WhBrBl G| Resistor,  91MΩ 5% |
| W | 1 | BrRdGr G | Resistor, 1.2MΩ 5% |
| X | 1 | Unmarked | Reset button |
| Y | 2 | Unmarked | Power jacks (banana clips) |
| Z | 2 | Unmarked | Serial and parallel ports |


Notes:

* This NV-RAM (B) from Goldstar has been discontinued. 117 left available in Europe.
* DUART (G): bidirectional 8-bit data bus, 2 COM ports, 6-bit parallel input, 8-bit parallel output. Parallel input pins are multi-purpose.
* Only 7 of the 8 DIP switches (R) are usable. (Why?)

## Addressing

| Address | Description |
| ------- | ----------- |
| 0x00 - 0x?? | ROM |
| 0x?? - 0x?? | RAM |
| 0x?? | Serial |
| 0x?? | Parallel |
| 0x?? | LED / Dice |
| 0x?? | Jumpers |


## Working status



