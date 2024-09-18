# Ponder

!>This documentation is not yet built

This board is primarily designed to act as a 6-way isolated USB-UART bridge using the RP2350. This can be used to interface to multiple devices-under-test simultaneously.

Unlike FTDI devices, no additional drivers are required to be installed in order for the device to function as a UART to USB bridge; Support is baked in to modern operating system kernels using USB CDC ACM.

In short, it is a quick and convenient way to debug devices via UART. No need for multiple cables and isolators.

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

The baseline design references [the minimal reference](https://datasheets.raspberrypi.com/rp2350/hardware-design-with-rp2350.pdf) from Raspberry Pi.
