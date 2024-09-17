# Design

## Appearance

![Front of board](./assets/v1.0/Ponder-front.png ':size=300') ![Back of board](./assets/v1.0/Ponder-back.png ':size=310')

## Interfaces

The following sections will cover detail of various interfaces across the board.

>[!TIP]
>I _try_ to maintain the logic of not having `hot` pins.  
>This means that where possible, anything providing a supply voltage will be in the form of a socket. Conversely, anything to be supplied a voltage will be presented as a header.  
>N.B. J10 is shown in renders as a header - It is a socket in the BoM. Its selection jumper, J9, is a 1.27 pitch for convenience.

### Buttons

#### BOOT

The BOOT button is used to put the MCU into USB bootloader mode in order to load *.UF2 files. Simply hold the button whilst powering on the board, then the board will present as a mass-storage device.

>[!TIP]
>Once booted, the button can act as a user input connected to `GPIO3`.

#### RESET

The reset button resets the device

### USB (J1)

The USB-C connector provides power to the board and is the primary mechanism for programming the board.  
Doing the boards intended use-case, the USB connector is also used for the data handling for the CDC ACM endpoints (i.e. your PC providing multiple COM ports for accessing each of the UARTs on-board).

---

### Isolated UARTs (J2, J3, J4, J5, J6, J7)

The isolated UARTs are provided by six 4 pin, 2.54 pitch, headers around the edge. The isolators connected to these headers `must` be fed with a voltage and ground by __each__ device under test, otherwise the UART comms will not be passed to the MCU.

- Supply voltage on VCC for `UART`[`0` .. `5`] is 2.375 .. 5.5V  
   - The isolators are also providing level translation and will support logic from 2v0 to 5v5.

>[!NOTE]
>If you require 1v8 logic -> A drop-in replacement isolator is the [MAX12931](https://www.analog.com/media/en/technical-documentation/data-sheets/max12930-max12931.pdf).  
>This part is significantly higher cost, hence not the default.

---

### I2C / SPI / Breakout (J8, J11, TPs)

The board includes some additional connection options for users to experiment with.

#### J8

J8 _nominally_ provides access to either `SPI0` _or_ `I2C0` & `IC21`. Additionally, the header provides 3v3 supply and GND connections.

J12 .. J15 provides optional pull-up / pull-down configuration for each pin by jumpering the desired end to the centre pin.

>[!TIP]
>These pins could be used for GPIO.

#### J11

On J11 there are 4 pins available for GPIO.

#### Test Points

The board includes a few test points which could be used for more signals if required.

1. 5, 6, 7, 9 are available for GPIO.
1. 40, 41, 42 are available for ADCs.
1. Programming test points are grouped near the MCU.

### VOut (J10)

J10 is provided as a convenient power access for lower power devices or for monitoring supply voltages.  
The voltage on J10 can be selected, using J9. The options are 3v3 or USB.

>[!NOTE]
>J10 _could_ be used to power the board via up-to 20V, when jumpered to USB, or a direct 3v3, bypassing the LDO (U1), if required.

---

## Bill of Materials

The below is an embedded version of the interactive bill-of-materials.

[ibom](./assets/v1.0/ibom.html ':include :type=iframe width=100% height=800px')

---

## Schematic

Whilst the majority of the expanded headers are self explanatory, the following is embedded to provide a fuller picture of the board.

```pdf
./assets/v1.0/ponder.pdf
```

## Miscellaneous

The following lists any miscellany.

### Mod Strikes

On the rear of the board, there is a 'MODIFICATIONS' box for tracking board revisions via modification sheets, each assigned a number.
When a board is updated to a particular modification level, mark the corresponding box.

Alternatively, if a board is used in a bespoke way, check the '/CTRLD' box to indicate it is not at a known or controlled build level.
