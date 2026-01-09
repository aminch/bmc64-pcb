# BMC64 PCB (Longboard)

This Longboard README details how to build or [modify](MODIFICATIONS.md) the v 2.0.5 of the BMC64 PCB. The longboard is effectively **DEPRECATED** for now, and won't get any more updates. Go [here](README.md) for the latest board.

The features the longboards are missing are:

 * Limited to USB 2.0 extensions (but this probably has zero practical effect)
 * Doesn't support [Mechboard 64](https://www.retrofuzion.com/products/mechboard-64-fully-backlit) without [modification](MODIFICATIONS.md) 
 * C64P stuck on firmware v3.0 without [modification](MODIFICATIONS.md)
 * See [History](README.md#history) for any future updates

These are not deal breakers if you are using an original C64 keyboard and BMC64, but if you are building a new board it is recommended to jump back to the main [README](README.md) and build the latest revision.

If there is interest in the longboard I can look into bringing it back in the future. Create an issue if you're interested and let me know why you would prefer this longboard. 

---

- [BMC64 PCB (Longboard)](#bmc64-pcb-longboard)
  - [PCBs \& Parts](#pcbs--parts)
    - [Main PCB - Longboard](#main-pcb---longboard)
    - [MicroSD card adapter board](#microsd-card-adapter-board)
    - [BOM](#bom)
    - [Ordering PCBs](#ordering-pcbs)
    - [Schematics](#schematics)
  - [Assembly](#assembly)
  - [Software](#software)
    - [Alternative software](#alternative-software)
    - [Compatibility](#compatibility)
  - [History](#history)
  - [Disclaimer](#disclaimer)


## PCBs & Parts

### Main PCB - Longboard

![BMC64 PCB](images/bmc64-pcb-v2.0.5.png)

### MicroSD card adapter board

 The adapter board is used to connect the MicroSD slot on the Raspberry Pi 3B+ to the main PCB

![MicroSD card adapter](images/MicroSD-adapter-pcb-v1.1.png)

### BOM

Full [BOM (Longboard)](bom/longboard-bom.md) of parts needed.

### Ordering PCBs

I ordered the PCBs via [JLCPCB](https://jlcpcb.com/) with just the standard settings. The main PCB was the standard 1.6mm thick, but it is important to order the MicroSD adapter board in **0.6mm** or **0.8mm** thick or it will be too big to fit into the microSD slot on the Raspberry Pi 3B+!

Check the [Releases](https://github.com/aminch/bmc64-pcb/releases/tag/V2.0.5), or `gerbers` folder for the gerber files.

### Schematics

![BMC64 PCB Schematic](schemantics/Schematic_BMC64-PCB-V2.0.5_2025-08.png)

![MicroSD card adapter](schemantics/Schematic_MicroSD-Adapter_2025-07.png)

## Assembly

The first step in assembly is to attach the microSD adapter board. We will do this by inserting the adapter into the Raspberry Pi 3B+, loosely assembling it in place, then tack soldering the adapter board to the correct location:
 
 * Attach the M2.5 nylon stand-offs to the four corners on the board where the Raspberry Pi 3B+ will be mounted.
 * Cut two 1x4 sets of header pins from the 1x20 header pins in the [BOM](bom/bom.md).
 * Slide the MicroSD adapter into the Raspberry Pi 3B+.
 * Place the 2 sets of 1x4 headers on the main PCB.
 * Place the Raspberry Pi 3B+ on the nylon stand-offs while inserting the header pins into the MicroSD card adapter.
 * Put one (or more) screws into the Raspberry Pi 3B+ to hold everything in place.
 * Place solder on the outer pins on top to holder the header pins in place
 * Flip the board and solder the outer pins on the headers too.
 * Flip the board and carefully remove the Raspberry Pi 3B+, and it should look like the picture below.

![MicroSD card adapter positioning](images/microsd-adapter-position.jpg)

 * Confirm that the positioning is ok by placing the Raspberry Pi 3B+ back on the adapter.
 * Adjust the board if needed by reheating the solder on the pins until you're happy.
 * Remove the Raspberry Pi 3B+ again.
 * Complete the final soldering on all of the header pins.

All of the other parts are labelled on the board. Start with the smallest components and work your way up until everything is attached. The list of parts to attach are below and the finished board should look as in the picture:

 * USB-C power port, 2x 5.1K resistors and 2x 0.1µF capacitors
 * Main power switch and fuse
 * 2x DB9 joystick ports and IC Regulator 
 * GPIO header
 * 390ohm resistor & 1x3 LED header
 * 4x USB ports
 * 1x20 header pins (for C64 keyboard)
 * 2x 1x20 female headers for mounting the Raspberry Pi Pico
 * MicroSD card slot
 * 1x6 female header for FTDI232 debug points (optional)

![BMC64 PCB](images/bcm64-pcb-v2.0.1.jpg)

You'll need to flip the board for the final components

 * 4x TVS diodes in the ESD1-4 positions next to the joysticks

![BMC64 PCB](images/bcm64-pcb-bottom-v2.0.1.jpg)

To assemble the final parts:

 * Push the Raspberry Pi Pico into the female headers on the board.
 * Attach the Raspberry Pi 3B+ to the nylon stand-off with screws being careful to slide in the microSD card adapter in the process.
 * Attach the Raspberry Pi Pico to the Raspberry Pi 3B+ with a short usb micro-A cable.
 * Connect the two USB_EXT ports to one of the Raspberry Pi 3B+'s usb ports with the short usb A-A cables.
 * Connect the Raspberry Pi 3B+ to the GPIO connector with the 40pin GPIO ribbon cable. (Note: Cut the cable to suit if desired)
 * Replace the plastic switch on the main switch with the smaller one included in the [BOM](bom/bom.md). (This is needed for the switch to fit correctly in the hole in the C64 case)
 * The finished board should be ready to drop into the case! It should look like it does below:

Note: Image below shows v2.0.1, MicroSD card slot & USB ports are repositioned in v2.0.5 (See: [PCB](images/bmc64-pcb-v2.0.5.png))

![BMC64 PCB with Raspberry Pi](images/bcm64-pcb-with-pi-v2.0.1.jpg)

The fitment of the board inside a C64C case is shown also shown above. All ports, the power switch and USB-C power connector use the existing holes in the case. It is mounted using screws to the existing stand-offs inside the case. It has mounting holes compatible with the breadbin and C64C cases.

## Software

Longboards have the Unversioned C64P PCB revision. You **MUST** use the v3.0 [_legacy_](https://github.com/aminch/c64p/releases/download/V3.0/c64p_legacy_default.uf2) build of the uf2 firmware as the C64P doesn't support anything else without [modification](MODIFICATIONS.md).

See: [Software](README.md#software) for all other details.

### Alternative software

See: [Alternative Software](README.md#alternative-software) for more details.

### Compatibility

The table below shows the pcb hardware and software compatibility:

| Component              | PCB V2.0.5 | PCB V2.0.4 | PCB V2.0.1 | PCB V1.2x |
| ---------------------- | :--------: | :--------: | :--------: | :-------: |
| MicroSD Adapter 1.0    |      ✗     |      ✓     |      ✓     |     ✓     |
| MicroSD Adapter 1.1    |      ✓     |      ✓     |      ✓     |     ✓     |
| C64P                   |      ✓     |      ✓     |      ✓     |     ✓     |
| Pi 3B/3B+              |      ✓     |      ✓     |      ✓     |     ✓     |
| Pi 4B                  |      ✓     |      ✗     |      ✗     |     ✗     |
| Pi 5                   |      ✓     |      ✗     |      ✗     |     ✗     |

* C64P requires firmware uf2 named _legacy_ for v3.0, and is not compatible with any higher version without [modification](MODIFICATIONS.md).

## History

See [History](README.md#history) for full details

## Disclaimer

This project is just a fun personal experiment for education and is not intended for professional or commercial use. I'm not an electrical engineer, so please use any information, code, or designs here at your own risk. 
