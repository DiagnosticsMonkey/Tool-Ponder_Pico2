# Ponder

!>This documentation is not yet built

This board is primarily designed to act as a 6-way isolated USB-UART bridge using the RP2035.

## Why?

1. Ground Loops -> Devices connected via UART may have different ground potentials. Without isolation, this could cause ground loops, which can lead to noise, signal integrity issues, or in severe cases, damage.
1. Damage to Equipment -> An isolated adapter prevents high-voltage from being passed to the USB port of the host computer.
   1. e.g. If you have a battery powered device and you're low-side switching, the product will float to the pack voltage when 'off'. This could damage any connected equipment due to the potential difference.
1. Noise Reduction -> Isolation reduces electrical noise, improving signal integrity and communication reliability.
1. Safety -> Protects the user, and equipment, when working with high-voltage or hazardous devices.
   1. N.B. electrical isolation should be verified by an electrical safety team before being used as a safety device.
1. Improved Debugging -> Issues with one device, shouldn't be able to impinge on the UART comms of another under test.

## Naming

Named after [Ponder Stibbons](https://wiki.lspace.org/Ponder_Stibbons), Head of Inadvisably Applied Magic, and Reader in Invisible Writings.

## Attribution

The baseline design references [the minimal reference](https://datasheets.raspberrypi.com/rp2350/hardware-design-with-rp2350.pdf) from Raspberry Pi.
