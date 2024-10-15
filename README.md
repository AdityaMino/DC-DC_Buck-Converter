<p align="center">
	
  [![Proteus](https://img.shields.io/badge/Proteus-%230079C1.svg?style=flat&logo=proteus&logoColor=white)](https://www.labcenter.com/)
	
  [![Arduino IDE](https://img.shields.io/badge/Arduino%20IDE-%2300979D.svg?style=flat&logo=arduino&logoColor=white)](https://www.arduino.cc/)
</p>

# DC-DC Buck-Converter
The name “Buck Converter” presumably evolves from the fact that the input voltage is bucked/chopped or attenuated, in amplitude and a lower amplitude voltage appears at the output. An external diode, together with an external inductor and output capacitor, produces the regulated DC output. Buck or step-down converters produce an average output voltage lower than the input source voltage. 

A DC-DC converter is essentially a constant power supply that is small, lightweight & highly efficient and uses a semiconductor switching element. Voltage in this type of converter is controlled through switching by storing energy in the circuit and releasing it afterward to output at a given voltage level. 
This conversion method is more efficient than voltage division, where unwanted power is dissipated as heat. It can respond quickly and suitable to changes in input voltage within the scope of normal operating conditions to return to the normal operating state. It is comprised of –

1.	 Switching power supply unit which, can turn ON/OFF switching elements that can be turned ON/OFF at high frequency to convert a DC input voltage Vin into a DC output voltage Vout.
	 
2.	A control unit, which is used to control the ON/OFF operation of the switching element of said switching power supply unit.

## Introduction
![image](https://github.com/user-attachments/assets/2e7f7710-cdb4-4996-8eba-17bf39216707)
Basic Block Diagram of Buck Converter

The Buck converter is the most widely used for traction motor control in electric automobiles, mine haulers, marine hoists, trolley cars, and forklift trucks. The buck converter is also called a step-down. In this project, we are going to make a Buck Converter Circuit using Arduino and N-Channel Power MOSFET (540N) with a maximum current capacity of 33 A. We are going to step down 12V DC to around 5.5-6V. Digital control design is done with use of Arduino Uno microcontroller. This microcontroller is used to produce Pulse Width Modulation (PWM) signal with constant duty cycle to drive the switch of the converter. The switch then will alternate turn the converter on and off to produce regulated voltage.

## Methodology 

The implementation of a DC-DC buck converter involves a systematic methodology that comprises several key steps to ensure its successful design and execution. The following steps are followed -

1.	Firstly, a thorough analysis of the application requirements is conducted to determine the input voltage range, output voltage and current specifications, efficiency targets, and any other relevant parameters. 
2.	Based on these requirements, appropriate components such as the switching device (typically a MOSFET), inductor, capacitor, and diode are carefully selected, considering factors like voltage and current ratings, switching frequency, and component availability. 
3.	Following component selection, detailed calculations are performed to determine various parameters of the buck converter, including the duty cycle, inductor value, and output capacitor size, ensuring compliance with the design specifications and efficiency goals

![image](https://github.com/user-attachments/assets/f1df633c-07cc-4f9e-ac54-71845b35eaf9)
Waveforms of the Buck Converter

Analysis of the buck converter begins by making these assumptions:
1.	The circuit is operating in a steady state. 
2.	The inductor current is continuous (always positive)
3.	The capacitor is very large, and the output voltage is held constant at voltage Vo. This restriction will be relaxed later to show the effects of finite capacitance.
4.	The switching period is T; the switch is closed for time DT and open for time (1-D) T. 
5.	The components are ideal. The key to the analysis for determining the output Vo is to examine the inductor current and inductor voltage first for the switch closed and then for the switch open. The net change in inductor current over one period must be zero for steady-state operation. The average inductor voltage is zero.

## Design Specifications
The design process begins with establishing the requirements for the buck converter, including input voltage range, output voltage and current, efficiency targets, and load regulation. For example, in our project, the input voltage is 12 V and the output voltage required is 5V with a maximum load current of 1A, these specifications will guide the design process.

![Simulation in Proteus](https://github.com/user-attachments/assets/a8630a2d-694a-4d1d-88eb-cbc7dda3ada6)
Circuit Simulation in Proteus

The buck converter should be controlled and match the specifications design and the converter should be resistant to changes in the load and reference voltages. The buck converter should meet the desired range of specifications-

1.	Frequency switching - 1KHz to 400 KHz 
2.	Inductance - 0.001mH to 20mH 
3.	Capacitor - from 0.001mF to 5mF
4.	Voltage ripple should be 0.9%. 
5.	Current ripple of 0.9%.

Hence the required equations for the design specifications of the buck converter are-

a)	Output voltage:	 Vo= Dr X VIN
			  **Vo=0.5*12 = 6 V**

b)	P-to-P ripple in capacitor voltage:	
			**∆VC = [VIN X Dr ( 1 – Dr)] / 8LC fsw^2
			∆VC = 0.831 %**

c)	Inductor current (∆IL ): 	
			**∆IL = [VIN X Dr (1 - D r )] / fsw L 
			∆IL = 60 mA**

d)	Maximum and minimum current of inductor: 							
      **IMAX = IO+ VOTOFF / 2 L 
			IMIN=IO–VOTOFF / 2L 
			IMAX = 120 mA
			IMIN = 0 mA**

e)	Determination of inductance: 	
			**L = [R X (1-D)] / 2fsw
			L= 2.71 mH**

f)	Determination of capacitance: 
			**∆VC = VIN Dr ( 1 – Dr) / 8LC fsw^2
			C = 100 uF**

## RESULT ANALYSIS

In our project, we have designed a basic DC-DC Buck converter using the following components-
1.	Arduino Uno Microcontroller -1
2.	IRF 540N Power MOSFET -1
3.	LM741 Op-Amp – 1
4.	Resistors (100, 330, 0.9 k ohm)
5.	Schottky Diode
6.	Inductor 
7.	Electrolytic Capacitor
8.	LED

We have made use of the Arduino to provide a PWM square wave of 5V and 50% Duty cycle as input to the LM741. The LM741 amplifies the voltage value from 2.5 to around 11 in the Non-Inverting Configuration.

Since our resistor value of Rf and R1 are: R1 = 330 ohms 		Rf= 1.1k ohms

Hence the Gain from the Op- Amp turns out to be = (1 +Rf/R1) = 4.3333

Hence the output voltage from the Op- Amp = 4.3333 * 2.5 =10.8333 V

Expected Output at the Load Voltage = 10.833/2 = 5.41666 V

![image](https://github.com/user-attachments/assets/1a263f78-14ba-4960-a30e-82355a457d98)
Inductor Voltage Waveform

- Input Voltage = 2.5 V
- Voltage after Amplification = 12.2 V
- Output Load Voltage = 5.5 V
- Gain = 4.88
- Hence, we were successfully to first amplify the low-voltage Arduino PWM to 12 V and then chop it down to nearly 6 V

![image](https://github.com/user-attachments/assets/6f3971f8-24cf-4150-8149-136f9cdcce26)
Output Voltage Waveform

In this project, we observed different waveforms through different switching frequencies. We also observed the led in a glowing position. The operating frequency determines the performance of the switch.
Switching frequency selection is normally determined by efficiency requirements and circuit parameters. At higher frequencies the switching losses in the MOSFET increase, and therefore reduce the overall efficiency of the circuit.
We infer the following from the Proteus simulations and the DSO –
- The Load Voltage exhibits a transient waveform and gradually settles into a steady state at about 8ms. The Voltage varied between 5.98 and 5.92, hence the average voltage was 5.95 V
- The Inductor current rises to Imax at a rate of (Vin – Vout)/2 and then reduces to Imin at a rate of Vo/2.
- The Capacitance is kept large enough such that the voltage ripple is minimal and load voltage does not fluctuate significantly during switching.
- In an ideal case, there is no drop across the circuit, but in our hardware, we have voltage drops across the switch and diode under operation.

## Conclusion & Project Images
![image](https://github.com/user-attachments/assets/7c211465-1363-489e-90f1-05210c275138)
Hardware Circuit of Buck Converter

The design process for a DC-DC buck converter involves careful consideration of specifications, component selection, calculation of parameters, simulation, practical implementation, and performance evaluation.
By following a systematic approach and addressing challenges effectively, a well-designed buck converter can be developed to meet the needs of various applications. 

In this work, Buck converter is analysed, designed for low output voltage ripple (0.840 %) with the output voltage of 5.9 volts. The circuit has been simulated using Proteus software and then hardware has been developed & controlled by Arduino Uno Microcontroller. The simulation results and experimental results are almost in agreement with each other.

![image](https://github.com/user-attachments/assets/1972b71d-bc6a-48bb-8382-8dffde6fd8b8)
Arduino Input PWM at 9.2 KHz

![image](https://github.com/user-attachments/assets/bc91fd10-2575-401f-8c01-893e9a56366d)
LM741 amplified output

![image](https://github.com/user-attachments/assets/14c3d86d-272f-4d84-9f7e-333ccd2a7fd6)
Output Load Voltage 


