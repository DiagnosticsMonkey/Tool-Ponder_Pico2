# Ponder - Pico 2

> [!WARNING]This documentation is not yet complete

This board is primarily designed to act as a 6-way isolated USB-UART bridge using the Pico 2. This can be used to interface to multiple devices-under-test simultaneously.

Unlike FTDI devices, no additional drivers are required to be installed in order for the device to function as a UART to USB bridge; Support is baked in to modern operating system kernels using USB CDC ACM.

In short, it is a quick and convenient way to debug devices via UART. No need for multiple cables and isolators.

> [!NOTE]
> This board is a variant of [Ponder](https://diagnosticsmonkey.github.io/Tool-Ponder/#/)  
> It exists due to a pro-tracted lack of consumer supply for the RP2350B, yet abundant supply of Pico 2's. I want to get software sorted.

---

## Why Isolated?

There are a few reasons why it can be a good idea to electrically isolate your device under test from your test system, including:

1. Ground Loops -> Devices connected via UART may have different ground potentials. Without isolation, this could cause ground loops, which can lead to noise, signal integrity issues, or in severe cases, damage.
1. Damage to Equipment -> An isolated adapter prevents high-voltage from being passed to the USB port of the host computer.
   1. e.g. If you have a battery powered device and you're low-side switching, the product will float to the pack voltage when 'off'. This could damage any connected equipment due to the potential difference.
1. Noise Reduction -> Isolation reduces electrical noise, improving signal integrity and communication reliability.
1. Safety -> Protects the user, and equipment, when working with high-voltage or hazardous devices.
   1. N.B. electrical isolation should be verified by an electrical safety team before being used as a safety device.
1. Improved Debugging -> Issues with one device, shouldn't be able to impinge on the UART comms of another under test.

### Why not isolate the USB

By isolating the individual UARTs you're able to connect to different voltage domains simultaneously. This means that Ponder can be installed as part of a debug or test ecosystem for a full product comprising of multiple referencing domains.  
The downside is that even if you're communicating with several UARTs on the same board, each isolator requires its own voltage feed. 

---

## Naming

Ponder is named after [Ponder Stibbons](https://wiki.lspace.org/Ponder_Stibbons), Head of Inadvisably Applied Magic, and Reader in Invisible Writings.

Ponder Stibbons is from the [Discworld universe](https://wiki.lspace.org/Discworld_(world)), brought in to existence by [Sir Terry Pratchett](https://wiki.lspace.org/Biography).

---

## Attribution

- Pico footprint from ncarandini -> https://github.com/ncarandini/KiCad-RP-Pico
  - Modified to add Pico 2 TPs and adjust USB mount holes
- Raspberry Pi - Pico 2 model used is originally by DrakerDG -> https://www.tinkercad.com/things/4xIXctwrZsr-raspberry-pi-pico-2
  - Modified to add TPs https://www.tinkercad.com/things/fXc3pdA6Lbr-raspberry-pi-pico-2-w-tps-rough
  - Converted from `OBJ` to `WRL` using -> https://imagetostl.com/convert/file/obj/to/wrl
  