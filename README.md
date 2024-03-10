# RadPie2040

A RP2040-based board, similar to [Raspberry Pi Pico H](https://www.raspberrypi.com/products/raspberry-pi-pico/), featuring:

- RP2040 microcontroller
- 16MB Flash
- breadboard-friendly pin headers with labels (+ debug header)
- USB-C connector
- BOOTSEL *and* RESET buttons
- **JLCPCB Assembly optimized**, 2-layer board
- KiCad 8 template, hierarchical schematic

**DISCLAIMER**: This board was designed as an exercise. It has not (yet) been manufactured and tested. Also, **I don't know what I'm doing**, this is like the third PCB I've designed. Don't use it lol.

| <a href="https://github.com/radex/RadPie2040/raw/main/assets/render.png"><img src="https://github.com/radex/RadPie2040/raw/main/assets/render.png" alt="Top down render of the board" width="300" /></a> | <a href="https://github.com/radex/RadPie2040/raw/main/assets/routing.png"><img src="https://github.com/radex/RadPie2040/raw/main/assets/routing.png" alt="PCB routing" width="300" /></a> | <a href="https://github.com/radex/RadPie2040/raw/main/assets/schematic.png"><img src="https://github.com/radex/RadPie2040/raw/main/assets/schematic.png" alt="Schematics" width="650" /></a> |
| -- | -- | -- |

## Credits and learning resources

This project is a fork of [Sleepdealr/RP2040-designguide](https://github.com/Sleepdealr/RP2040-designguide). It bears little resemblance to the original, but it was a great starting point (and still contains some pieces of it).

I also took a lot of inspiration and knowledge from these YouTube videos:

- [MicroType Engineering - RP2040 KiCad 6 Hardware Design](https://www.youtube.com/watch?v=RNH-CL8GrF8)
- [Phil’s Lab - Raspberry Pi RP2040 Hardware Design](https://www.youtube.com/watch?v=X00Cm5LMNQk)

There's extra learning resources in the `Resources/` folder (copied from Sleepdealr's project).

## Components

This board is optimized to use JLCPCB Basic (or Extended Preferred) components as much as possible to make it cheap to manufacture at 2-5 pieces scale.

Some worth mentioning:

- Flash: C97521 - Winbond W25Q128JVSIQ - 128Mbit (16MB) NOR Flash
- Voltage Regulator: C5446 - XC6206
- Crystal: C9002 - 12MHz
- Buttons: C318884 - TS-1187A-B-A-B
- TVS diodes: C7420376 - SRV05-4

Most components are the same as in [Sleepdealr's design](https://github.com/Sleepdealr/RP2040-designguide). Differences: larger Flash, different TVS diodes, added buttons, power LED indicator, removed resettable fuse.

**Extended parts**: The only parts that are not on JLCPCB's Basic parts list (i.e. you'll pay $3 feeder fee per part) are the RP2040 and the USB-C connector. (Pin headers are not on the BOM, but you can add them).

## Customizability

Some things to consider:

- The 0Ω 1206 resistor is a placeholder for a resettable fuse. (There are none in JLC's Basic parts, but it's a good idea to have one)
- Flash storage and buttons could be replaced with smaller physical packages
- For size/cost/simplicity, you can remove buttons, USB, TVS, fuse placeholder, LED if you don't need them. You could even remove the crystal and rely on RP2040's ring oscillator if you don't need precise timing or max performance

## TODO

- Have this board manufactured, see if it works!
- I'm concerned about the crystal, it seems to me that layout and loading capacitors could be better, but they can be finnicky, and Sleepdealr's design works, so I didn't change anything.
- I'm thinking of designing a smaller version, optimized for use as a module with carrier boards (using 1mm pitch pin headers, not castellated holes like the original Pico for cost reasons)

