---
title: "Märzhäuser EK 14 motorized stage adventures"
date: 2024-10-29
---

A really quick post today...

Got another nice upgrade for my microscopy setup: a Märzhäuser EK 14 motorized stage! It's a beast of German engineering in full metal, weighing *at least* one kilo. Mine came in a bit whacked out of squareness so I had to fix that first; it was also almost binding in the Y direction. Not good.

On the bottom, there are 2 groups of 2 smaller groups of 4 screws, situated to the left and right of the opening like this:

![Carriage mount screws](/blarg/assets/20241029/ek14-y-carriage-mount.jpg)

These are the screws to be undone to adjust the squareness. Once undone, the halves can be moved around; I got them in position I felt was right. It should be also possible to put the stage edge on a flat surface to aid positioning. I pressed slightly on the opposite end to where motors are to tension it a little bit and fastened the screws. After the adjustment the stage moves freely.

I thought I'd note down the connector pinout for motors etc for those not willing to undo the screws.

![Connector PCB, a mess of wires](/blarg/assets/20241029/ek14-connector.jpg)

The motor pinout could be found in their datasheet or by buzzing it out (black+green, red+blue are the winding pairs), but figuring out the other wires will take some work.

There are also two small hatches, they provide access to small endstop sensor PCBs for the X axis. On the PCB there are the sensor itself marked 506A which is [HAL506 by Micronas](https://www.mouser.com/datasheet/2/735/HAL501___507,_508,_509,_HAL516___519,_523_Hall-Eff-1109092.pdf), a capacitor, an LED, and a resistor. The capacitor is placed between brown and white wires, so these are likely power supply. The LED and resistor are in series and connected to the remaining wire so this is likely the output. Checking the datasheet, this seems to be correct: pin 1 is VDD, 2 is GND, 3 is OUT.

| Pin | Wire            | Signal    |
|-----|-----------------|-----------|
| 1   | X motor red     | Winding B |
| 2   | X motor blue    | Winding B |
| 3   | X motor black   | Winding A |
| 4   | X motor green   | Winding A |
| 5   | Y motor red     | Winding B |
| 6   | Y motor blue    | Winding B |
| 7   | Y motor black   | Winding A |
| 8   | Y motor green   | Winding A |
| 9   | XO green        | Output    |
| 10  | XO+XE white     | Ground    |
| 11  | YE blu/white    | Output    |
| 12  | YO+YE blk/white | Ground    |
| 13  | XE yellow       | Output    |
| 14  | YO grn/white    | Output    |
| 15  | All brown       | Power     |

Finally, XO is the rightmost, XE is the leftmost, YO is the innermost, and YE is the outermost position.

Up next, try to wire this up and see if it works!

XOXO,
/DJ
