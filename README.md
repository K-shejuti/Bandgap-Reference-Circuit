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

![BGR_Principle](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/edb023d4-39e9-4ecb-8402-3017330b75bc)

## CTAT Voltage Generation
Usually semiconductor diodes shows CTAT behaviour. If we consider constant current is flowing through a forwrard biased diode, then with increase in temp. we can observe that the voltage across the diode is decreaseing. Generally, it is found that the slope of the V~Temp is -2mV/deg Centigarde.

## PTAT Voltage Generation

![Equation](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/f63e6032-b1bb-4050-a046-72a327ec4791)

From Diode current equation we can find that it has two parts, i.e.

- Vt (Thermal Voltage) which is directly proportional to the temp. (order ~ 1)
- Is (Reverse saturation current) which is directly proportional to the temp. (order ~ 2.5), as this Is term is in denominator so with increase in temp. the ln(Io/Is) decreases which is responsible for CTAT nature of the diode.

So to get a PTAT Voltage generation circuit we have to find some way such that we can get the Vt separated from Is.
To get Vt separated from Is we can approach in the following way

![PTATCKT](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/ed891108-dc89-4082-bb0f-8ab2c75f8be3)

In the above circuit same amount of current I is flowing in both the branches. If somehow we make the node volatge at point A and B equal the voltage drop across the resistor will be proportional to Vt and independent of Is, so it is a PTAT.

![PTATEQN](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/472a00f1-fec8-41a1-8c3b-8bf943c7ed0e)

From above we can see that the voltage V-V1 is PTAT in nature, but it's slope is very less as compared to the CTAT, so we have to increase the slope. In order to increase the slope we can increase the number of diodes in parallel. Or a better way is to amplify the voltage V-V1 to get a higher PTAT slope.

![PTAT](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/9849f818-b79d-4030-b44a-67c13862eab9)

# Types of BGR:
1)Using Sself-biased Current Mirror
2)Using Operational Amplifier

Application wise BGR can be categorised as 
- Low-voltage BGR
- Low-power BGR
- High-PSRR and low-noise BGR
- Curvature compensated BGR

## 1)Self Biased Current Mirror based BGR

The Self-biased current mirror based constitute of the following components.
- CTAT voltage generation circuit
- PTAT voltage generation circuit
- Self-biased current mirror circuit
- Reference branch circuit
- Start-up circuit

### 1.1) CTAT Voltage Generation Circuit
The CTAT Voltage generation circuit consist of a BJT connected as a diode and a constant current is passed through it. The voltage across the diode  shows CTAT nature as explained above.

The Simulation is to show CTAT voltage.














  
