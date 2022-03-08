# Laser Engraving

## Types

[https://www.youtube.com/watch?v=Y7tknUioLwY](https://www.youtube.com/watch?v=Y7tknUioLwY)

* CO2
  * some CO2 can't mark steel, for this you need a fiber laser
  * you can mark anodized aluminum
* Fiber laser

## Flow

### Prep file

Use for example Inkscape to produce a PNG, or TIFF, or BMP, or other Raster images that are 1-Bit black and white camera ready artwork. No Gray scale. Should be in a minimum of 300 DPI resolution.

Or g code (thanks to some plugins).

### Prep material

{% embed url="https://kanyanaengineering.com.au/can-you-laser-engrave-stainless-steel#What_Is_the_Best_Method_to_Mark_Stainless_Steel" %}

### Prep modality

engraving vs etching  vs marking vs cutting

#### **Can Stainless Steel Be Laser Etched?** <a href="#can-stainless-steel-be-laser-etched" id="can-stainless-steel-be-laser-etched"></a>

Yes, stainless steel can be laser etched. Laser etching is less invasive than engraving, meaning less material is removed in the process.&#x20;

## Models

### Newbie models

* WAINLUX K6

### For steel

* ATOMSTACK S10 Pro 50W&#x20;
* ATOMSTACK A10 Pro 50w
* [ATOMSTACK X7 Pro 50W](https://youtu.be/NQoeYksA\_ao?t=418)
  * [https://youtu.be/wHlAXOrSHhw?t=498](https://youtu.be/wHlAXOrSHhw?t=498)
* Sculpfun S9 90W

{% hint style="info" %}
source: amazon review

Q: What is the difference between the S10 and X7?&#x20;

A: Based on what I have read, the S10 and the X7 are the same machine, just called different names in different markets (X7 in the US, S10 elsewhere)
{% endhint %}

## Information from pro players

From: Laser Lance (AKA Vasily Basov, former employee of Control Laser Corporation, part of Hans Laser, China)

{% hint style="info" %}
More important than the laser power is the per-pulse energy (PPE). PPE tells you more about the laser than just how much energy is in each pulse. Generally speaking, a laser with a PPE of under 1mJ indicates inferior fiber; the pulse energy is managed to reduce the liklihood of fiber damage caused by the laser being absorbed by fiber impurities. How do you know what the PPE of the laser is if it's not listed in the specification sheet? Divide the maximum power by the lowest Pulse Repetition Frequency (PRF) for a Q-switched laser (optimum pulse repetition frequency (PRFo) for MOPA), and you get the approximate PPE, i.e., 20W / 20,000 = 0.001J = 1mJ. I would not buy a fiber laser that has a PPE under 1mJ.

Another advantage MOPA has over a Q-switched fiber laser is the ability to go below the optimized pulse repetition frequency (PRFo). PRFo is the frequency where both pulse energy and power are at their maximum. Below PRFo, power is reduced approximately linearily, and pulse energy is usually capped at the maximum (fun fact, in diode-pumped open-air lasers, pulse energy increases below PRFo). Since we consider power to be "heat", we're effectively engraving with a lower heat affected zone (HAZ), which means better cuts--typically we want high PPE to engrave, and power (heat) to mark/anneal. Combine this with the ability to modify the pulse width, or the time each pulse interacts with the material, and we have complete control over the application.

Why can't you anneal with a Raycus laser? The IPG laser systems Control Laser Corporation (CLC) was selling when IPG came out with their 20-Watt laser came with a Linos 254mm Focal Length (FL) lens, having a 7-inch field. These are 1mJ lasers, and are very capable of annealing with the correct parameters. I would argue that the Raycus systems likely have a cheap Opex lens, and this, combined with the low PPE is why these lasers have difficulties annealing. The Opex lens resolving power is crap; there is no discernable airy disc with these lenses; the laser is diffused too much, causing energy density to suffer. A Linos or Rofin-Sinar lens, having that large 120mm output lens, have wonderful resolving power, and this is why the IPG 20Watt laser, having a maximum frequency of 40kHz, can anneal all day long without problems. Yes, the Linos lens is about $1,600 more than the \~$50 Opex lens, but when you consider that you need to add more power with the Opex lens to get the same effect (energy density) as the Linos lens, it's cheaper to buy an expensive lens than to buy a laser with more power. Also important is the size of the laser beam going into the focus lens, as this is one of the parameters to the spot size algorithm. If the beam is small going into the lens, the spot will be large, i.e., low energy density. However, if the beam is large going into the focus lens, the spot will be small, high energy density. So, it's important to consider the complete system when talking about capabilities and applications, and comparing between systems. Stick a Linos lens on that Raycus, expand the beam to 8mm, and see what happens!

Finally, I want to clarify that IPG is originally a Russian company, that moved the headquarters to Massachusetts to have a better political environment to operate in. Yes, there are factories in Germany, and still in Russia, and yes, those Chinese systems that claim to have IPG lasers in them are really IPG lasers (manufactured in Russia). Most general purpose fiber lasers from IPG are manufactured in Germany, and I think that's what you meant to say; i.e., the German IPG fiber is the holy grail of q-switched fiber lasers. (For MOPA, SPI Lasers, now part of Trumpf, is the equivalent).
{% endhint %}











