# Penguin
## A Redox compatible low profile keyboard with per-key RGB

### Parts

- Kailh Choc Switches x 70
- Kailh Choc Keycaps x 70
- Sk6812 mini-e RGB LED\* x 70
- 1n4148 smt sod-123 package diode x 70
- TRRS connector x 2
- 4 pin through-hole tactile switch x 2
- 680 ohm 0608 package resistor\*\* x 2
- Arduino Pro Micro x 2
- TRRS cable x 1
- USB cable for the arduino x 1

\* The type I designed the keyboard for doesn't match the datasheet exactly for
whatever reason, [try getting something that looks like this one](https://www.aliexpress.com/item/4000475685852.html)

\*\* Should work without any resistors if you just bridge their place instead,
but no guarantees

### Keymaps

Should work with any keymap that was made for the redox series.

### Assembly

The keyboard PCB, just like the Redox PCB is double sided. The only component
that goes on the backside are the diodes. This was done to make the board itself
as thin as possible. The rest of the components mount on the topside.

Start with the microcontroller, the resistor and the RGBs. This is necessary,
because soldering the RGB LEDs can be finicky and you'll want a way to test if
you've connected them successfully, which can be done by flashing the
microcontroller. Check each time that's the switches can sit flush on top of the
LEDs, otherwise the whole switch might end up crooked. 

Afterwards it's best to go from smallest to biggest like usual, first the diodes
on the back, then the tactile switch and the TRRS connector and finally the
switches themselves.

### Flashing

By default the keyboard is set to use EEPROM handedness check, this means that
for the first time for both halves the following commands need to be used:

```
make penguin:default:avrdude-split-left
make penguin:default:avrdude-split-right
```

afterwards the end part can be dropped, when flashing again.
