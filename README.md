# Bandgap-Reference-Circuit
This github repository is for the design of a Band Gap Reference Circuit (BGR) using Google-skywater130nm technology PDK.
# Introduction to BGR
The Bandgap Reference (BGR) is a circuit which provides a stable voltage output which is independent of factors like temperature, supply voltage.

![BGR1](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/c20aae7b-f2b2-48e9-90df-75ae3d911fc2)

Why BGR

- A battery is unsuitable for use as a reference voltage source.voltage drops over time

- A typical power supply is also not suitablenoisy output and/or residual ripple.
  
- A voltage reference IC used buried Zener diode,Discrete design required additional components and high frequency filtering circuits due to higher thermal noise.
Low voltage Zener diode is not available

Solution

- A Bangap reference which can be integrated in bulk CMOS, Bi-CMOS or Bipolar technologies without the use of external components.
# Features of BGR
- Temp. independent voltage reference circuit widely used in Integrated Circuits
- Produces constant voltage regardless of power supply variation, temp. Changes and circuit loading
- Output voltage of 1.2v (close to the band gap energy of silicon at 0 deg kelvin)
- All applications starting from analog, digital, mixed mode, RF and system-on-chip (SoC).
# Applications of BGR
- Low dropout regulators (LDO)
- DC-to-DC buck converters
- Analog-to-Digital Converter (ADC)
- Digital-to-Analog Converter (DAC)
# BGR Introduction
The operation principle of BGR circuits is to sum a voltage with negative temprature coefficient with another one exhibiting opposite temperature dependancies. Generally semiconductor diode behave as CTAT i.e. Complement to absolute temp. which means with increase in temp. the voltage across the diode will decrease. So we need to find a PTAT circuit which can cancel out the CTAT nature i.e. with rise in temp. the voltage across that device will increase and thus we can get a constant voltage reference with respect to temp.
  
