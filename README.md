# Bandgap-Reference-Circuit
This github repository is for the design of a Band Gap Reference Circuit (BGR) using tsmc 180nm technolodgy.
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

<img width="490" alt="ctat_ciruit" src="https://github.com/user-attachments/assets/ad6350b9-cc5e-465a-889e-bcdaa1bd7c01" />

<img width="758" alt="ctat_simulation" src="https://github.com/user-attachments/assets/40ec1ce0-95b3-4eea-b713-bff4bf669fb9" />


### 1.2) PTAT Voltage Generation
As dicussed above we can get PTAT voltage by taking a difference between the votage of 1 diode and n diodes, for simple simulation we are taking n=2. but in general n=8 is taken.

<img width="736" alt="ptat_plot" src="https://github.com/user-attachments/assets/65a4e846-2624-492c-b274-36c613e954f1" />

We can observe from Simulation that the slope of PTAT voltage is much lesser than the slope of CTAT voltages.

### 1.3) Self-Biased Current Mirror Circuit

he Self-biased current mirror is a type of current mirror which requires no external biasing. This current mirrors biases it self to the desired current value without any external current source reference.

Below is the simulation of it

<img width="513" alt="ptat_circuit-current_mirror" src="https://github.com/user-attachments/assets/5f3861fa-caf4-40e4-b20a-772a59626af5" />

### 1.4)Reference Branch Circuit

The reference circuit branch performs the addition of CTAT and PTAT volages and gives the final reference voltage. We are using a mirror transitor and a BJT as diode in the reference branch. By virtue of the mirror transistor in the reference branch the same amount of current flows through it as of the current mirror branches. Now from the PTAT circuit branch we are getting PTAT voltage and PTAT current. The same PTAT current is flowing in the reference branch. But the slope of PTAT voltage is much smaller than that of slope of CTAT voltgae. In order to make increase the voltage slope we have to increase the resistance (current constant, so V increases with increase in R). Now across the high resistance we will get our constant reference voltage which is the result of CTAT Voltage + PTAT Voltage.

![refbranch1](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/ce9b3042-e429-4bb2-8120-60b018b1017c)

The whole circuit drawn is ltspice below:

<img width="581" alt="final_current-mirror-schematic" src="https://github.com/user-attachments/assets/47176385-36e3-4116-b6d2-d42fa830a345" />

Now we do know that slope of CTAT is greater than slope of PTAT, so we need to amplify our PTAT voltage, now voltage across the resistance R2= R2/R1*Vtln(n). R1 is used to fix the current in current mirror branch. We can either increase number of diodes in parallel or increase the R2 value, Here we will increase R2 to amplify our PTAT.

From the simualtion we can observe that when R2=110k ohm ,the CTAT and PTAT nearly cancels each other and we get the constant voltage  reference.

The below is the simulation for it:

![image](https://github.com/user-attachments/assets/b3de8b43-631e-42b7-802e-c97b6b3e900e)

But if we zoom in we can see a bell shaped curve and not a straight line. This is due to non linear nature of CTAT and PTAT.

![Screenshot from 2024-01-14 13-38-09](https://github.com/K-shejuti/Bandgap-Reference-Circuit/assets/152790020/c0f55229-d794-46be-a042-b83e2ab85153)


### 1.5 ) Varaible supply volatge:
 Till now we have only the the graphs with varying temperature from -40 to 125 degree celcius, Let us plot the ref voltage when supply is varying from 0 to 5V.

<img width="803" alt="supply variation" src="https://github.com/user-attachments/assets/1a48e457-8241-4881-a4f4-b92095802661" />


Inially for small value of the supply the mosfets are not in saturation. but after reaching a certain voltage all the Mos are in saturation and the reference voltage is again near to 1.2 V . So the circuit is also taking care of supply variation.

### 1.6) Startup Circuit:

Since the circuit is self baised we need a startup circuits. There are total two operating region

- Zero current region
- Normal operating region
Zero cucrent region is a stable operating region . so once the circuit enters this region it can't come out of the state without disturbance. but current in the circuit is zero ,so the circuit can't attend the desired reference This issue can only be observed in transient and when the supply has a finite delay and rise time.

<img width="794" alt="pulse input" src="https://github.com/user-attachments/assets/6522f254-f1e9-45c3-905b-307eb64bda57" />

<img width="734" alt="V-reference" src="https://github.com/user-attachments/assets/fef51f75-0942-467e-a97f-7f58eb8c263a" />

We can observe here that vref is reaching a maimum value of 450 mv.

The start-up circuit forecefully flows a slow amount of current through the self-biased current mirror when the current is 0 in the current mirror branches, as the current mirror is self biased this small current creats a disturbance and the current mirror auto biased to the desired current value.

Below is the circuit drawn is Ltspice. 

<img width="762" alt="startup_schematic" src="https://github.com/user-attachments/assets/087bbd6e-9165-4f8b-a44a-0683afbcccf1" />

The startup issue is solved and the circuit is again giving the desired vref value

<img width="847" alt="vref_with_startup" src="https://github.com/user-attachments/assets/767fc1e5-c7c8-4c11-9c80-27d8222533ec" />

This is the complete simulation of current mirror based startup circuit. 
































  
