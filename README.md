See also an rp2040 fork of this project:
https://github.com/JohnDMcMaster/rprl78-src

# Hardware setup

You need something like this:
* Two serial cables
  * serial-gpio: FTDI C232HM-DDHSL-0
    * TOOL0: green wire
    * RESET: gray wire
    * Ground: black wire
  * serial-uart: a second USB TTL serial cable, ideally non-FTDI (so its easier to identify)
    * Ex: https://www.adafruit.com/product/954
    * RX: white wire
    * TX: green wire
    * Ground: black wire
* RESET wiring
  * Add PU resistor
  * Add serial-gpio RESET line
  * Connect to MCU RESET line
* TOOL0 wiring
  * Add PU resistor
  * Add serial-gpio RESET line via diode (so that can pull down)
  * Add serial-uart TX line via diode (so that can pull down)
  * Add serial-uart RX line directly
* Noting
  * As long as serial-gpio TOOL0 is high or Z it won't contend with TOOL0
  * As long as serial-uart is idle (since NRZ) it won't contend with TOOL0

You will then need to connect this to your target board, such as by attaching to
a 14 pin Renesas emulator connector

# API / usage

This is really an expert use thing as written.
If you want more out of the box functionality, take a look at rprl78

