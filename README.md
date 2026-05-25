 1Zhako1.github.io
## Printed Circuit Board (PCB) Project

In this project I designed the PCB in EasyEDA with the given LT1490 Op-amp. I was given only the capacitor and Gain Vout/Vin values. I picked resistor values that would result in the expected gain.
![
### Op-Amp PCB Simulation & Hardware Verification

**The Problem & Constraints**
* **Objective:** To design, simulate, and physically verify an operational amplifier circuit on a custom PCB.
* **Safety Constraints:** To ensure the op-amp was not overloaded during testing, the supply voltages (VCC and VEE) were strictly limited to ±10V instead of the standard ±12V.

**Tools & Skills Demonstrated**
* **Software:** LTSpice, Microsoft Excel (Data Visualization).
* **Hardware:** Custom PCB, Rigol Oscilloscopes, Function Generators.
* **Core Concepts:** Frequency Response Analysis, Bode Plots, Signal Attenuation, Datasheet Interpretation.

**The Engineering Process**
* **Simulation Baseline:** I first modeled the circuit in LTSpice to establish a theoretical baseline for the expected frequency response.
  ![LTSpice Schematic](Screenshot2026-04-21152247.png)
*The schematic from LTSpice*
* **Physical Hardware Testing:** Once the PCB was assembled, I set up a lab test using a Rigol oscilloscope. I fed the circuit an input signal with an amplitude of approximately 1V (Vin = ~1.02V).
* **Frequency Sweeping:** I methodically swept the input frequency across 32 distinct intervals, starting at 60 Hz and pushing all the way up to 500 kHz. At each step, I logged the output voltage (Vout) and phase shift to calculate the physical Gain (dB).

**Visual Proof**

![Oscilloscope Capture](low.png)
*Oscilloscope capture showing a clean, low-frequency input and output signal.*
![Oscilloscope Capture](high.png)
*Oscilloscope capture showing a clean, high-frequency input and output signal.*
![Oscilloscope Capture](500.png)
*Oscilloscope capture showing a clean, 500kHZ-frequency input and output signal.*

![Oscilloscope Capture](replace-with-your-oscilloscope-image-filename.png)
*Oscilloscope capture showing a clean, low-frequency input and output signal.*

![Table: Measured & Calculated data](Table.png)
*Excel Bode plot directly comparing the LTSpice Simulated Gain vs. the Physical Measured Gain.*
![Bode Plot](dB.png)

![Bode Plot](degrees.png)


**Results, Learnings & Troubleshooting**
* **The Success:** Overall, the physical PCB functioned correctly and closely mirrored the LTSpice simulation across most of the frequency band.
* **The Anomaly:** During testing, I observed that the gain did not look correct at 25 kHz. Past this cut-off frequency, there was a drastic decrease in Vout, causing the gain to approach 0 as the frequency increased rapidly toward 500 kHz.
* **The Root Cause Analysis:** To understand this failure mode, I consulted the component's datasheet, specifically the "Undistorted Output Swing vs Frequency" graph. The data revealed that the op-amp cannot physically support large output-voltage swings at higher frequencies without severe distortion. This hardware limitation perfectly explained the drastic attenuation measured in the lab.
