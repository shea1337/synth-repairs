# Korg M1R Repair, May 2022

A customer brought me a M1r which could power on, but no audio could be heard through any of the outputs. The unit hadn't been used in approximately a year, and when it was last used it was producing audio normally. 

I found the following problems:

* Corrosive glue which had turned dark brown and had turned all metal it had come in contact with green
* Some parts on the power supply in the +/-12V path had failed completely
* Other parts had drifted too far off spec for comfort

Usually I would power on the unit to measure voltages etc, but it could clearly be seen that this was in no shape to power on, so I began going through the schematics and noting which parts had failed.

Even some ceramic capacitors on the primary side had been corroded by some glue, and were measuring 75-80% of their intended capacity, so I replaced those as well. These were C7 and C8, two 2200pF ceramics. I could only find 440V parts with the correct lead spacing, no problem there so I ordered those.

Two 560 ohm resistors in the +/-12V output path were reading something like 20 megohms and a 220 ohm was simply completely eaten away, looked like it failed spectacularly, could not be measured out of circuit.

The M1 / M1R power supply (USA/Japan version) uses a 100uF 200V capacitor on the primary side, two 2200uF 10v's, four 220uF 25v's and a 1uF 50v on the secondary. Everything got 105c 10000 hour caps except for the 2200uF's which I used 85c 10000 hour. One of the 2200uF's is very close to a diode bridge on a heatsink. I will explain my reasoning for this: the SMPS circuit used on this synth is not very dissimilar from the kind of SMPS found in a TV or compact personal computer. Many of the smaller caps, like the 220uF's, are jammed together in a corner and do not have ideal spacing to allow them to cool off. The 2200uF's are more spaced out, but one is placed right by a heat sink. While it may not be what Korg intended, I learned from an engineer who works on things like SMPS for TV's that one should reuse a cap of the same temperature rating in such a position. It is in effect a crude failsafe circuit if something is going very wrong. 

Consider that all the original caps used were 85C rated and would likely still be working fine if not for the corrosive glue. 85C (~185F) is a very high temperature and the difference between that and 105C (~220F) are not temperatures normally reached in the power supply of a synthesizer which is only putting out a small amount of power - often less than 40 watts. If the diode bridge's heatsink is reaching temperatures of over 85C, something is going _very wrong_ with the circuit. I also have found from my own experiments that, if a very high temperature rated capacitor is used in such a position, and there is a fault occurring, it will gladly continue supplying that power until seriously dangerous temperatures of 105C or even higher have been reached. For this reason, if the ability of the capacitor to output that much power was curbed well before reaching temperatures like 105C, there's a much better chance that the rest of the circuit (or one attached to it) won't be damaged. It's much easier to repair the power supply in that case. Given that often synthesizers of this era often have mains AC going directly to the power supply board without any fusing or filtering, it's important to consider possible external faults (like a power surge or brownout) and what will keep the synthesizer and its user safest. 

The +/-12V rails are really only powering the circuitry which is directly in the audio path, everything else in the M1R is running off 5V. The 5V circuit including the bigger 2200uF caps managed to escape the glue at the factory, so it makes sense that the audio wasn't able to pass despite the synthesizer being able to power on and appear to work normally. 

It is important to do the tedious work of checking resistances across the power supply before powering it on when something like corrosion occurs. These single sided power supplies use a lot of "staples" to join different sections of the power board, and enough corrosion can give these staples strange resistive properties when electricity is applied. For this reason I will replace any problematic staples with solid core wire of a similar gauge.

If it wasn't visually obvious that a good section of the power supply was ruined, I would have powered it on and tested voltages before anything else, where I would have seen there was an issue on either the +12V, -12V or both. This was nice and convenient since it's not common that the bulk of the diagnosis can be done visually. 