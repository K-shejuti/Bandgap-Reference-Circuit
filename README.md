# Bandgap-Reference-Circuit
This github repository is for the design of a Band Gap Reference Circuit (BGR) using Google-skywater130nm technology PDK.
# Introduction to BGR
The Bandgap Reference (BGR) is a circuit which provides a stable voltage output which is independent of factors like temperature, supply voltage.

![BGR1](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/c20aae7b-f2b2-48e9-90df-75ae3d911fc2)

Why BGR
A battery is unsuitable for use as a reference voltage source.

-voltage drops over time
A typical power supply is also not suitable
noisy output and/or residual ripple.
A voltage reference IC used buried Zener diode,
Discrete design required additional components and high frequency filtering circuits due to higher thermal noise.
Low voltage Zener diode is not available
Solution

A Bangap reference which can be integrated in bulk CMOS, Bi-CMOS or Bipolar technologies without the use of external components.
