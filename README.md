# esim-marathon
🕹️ Monostable Multivibrator using NE555 and Op-Amp (eSim Simulation)

📘 Overview

This project demonstrates the design and simulation of a Monostable Multivibrator circuit using an NE555 timer IC and an Op-Amp trigger conditioner in eSim (v2.5).
The circuit produces a single output pulse of fixed duration when triggered by a voltage pulse processed through the non-inverting op-amp stage.

It is designed and simulated using KiCad Schematic Editor and Ngspice in the eSim environment.

⸻

⚙️ Working Principle
	•	The Op-Amp is used as a signal conditioner to amplify or buffer the input trigger pulse (V2).
	•	The conditioned output from the op-amp drives the trigger input (Pin 2) of the NE555.
	•	When a low-going pulse is detected at the 555 trigger pin, it generates a HIGH output at Pin 3 for a duration T = 1.1 × R1 × C2.
	•	The output drives a MOSFET, which powers an LED, indicating the output pulse visually.

After time T, the output returns to LOW automatically, completing one monostable cycle.

⸻

🧩 Components Used

Component	Description
NE555D	Timer IC configured in monostable mode
Op-Amp (X1)	Non-inverting amplifier for trigger signal conditioning
R1	Timing resistor
C2	Timing capacitor
C1	Coupling capacitor for trigger input
V1	DC supply voltage (for 555 and op-amp)
V2	Input trigger voltage source
M1 (MOSFET_N)	Switches LED load during output HIGH
D1 (LED)	Indicates output pulse visually
A1 (OR Gate)	Logic control component (optional)
PWR_FLAG & GND	Power and ground references for simulation stability


⸻

🧮 Time Period Formula

T = 1.1 \times R1 \times C2

Where:
	•	R1 = Timing resistor (Ω)
	•	C2 = Timing capacitor (F)
	•	T = Output pulse width (seconds)

⸻

🔌 Circuit Block Diagram

            +VCC (V1)
               │
               │
         ┌────────────┐
         │  Op-Amp    │
         │ (X1 NonInv)│
         └────┬───────┘
              │  Amplified Trigger
              ▼
        ┌──────────────┐
        │   NE555D     │
        │              │
 Trigger ─►TRIG     OUT ├───>─┬──> MOSFET (M1) ───> LED (D1)
        │              │    │
        │   DIS, THR   ├────┘
        │              │
        └──────┬───────┘
               │
             GND (eSim_GND)

🟢 When the op-amp output triggers the NE555 → output goes HIGH → MOSFET conducts → LED glows for time T

⸻

🧠 Simulation Details
	•	Software: eSim 2.5 (KiCad + Ngspice)
	•	Simulation Type: Transient Analysis
	•	Suggested Parameters:
	•	Stop Time: 0.05s
	•	Time Step: 0.0001s

⸻

📊 Expected Output
	•	When the input (V2) changes, the op-amp converts it to a proper trigger signal.
	•	The 555 output (Pin 3) goes HIGH for the duration T = 1.1 × R1 × C2.
	•	The MOSFET turns ON and the LED glows briefly.
	•	After the delay, output returns LOW, and LED turns OFF automatically.

⸻

📂 Project Files

File	Description
kk.kicad_sch	KiCad schematic
kk.kicad_pro	Project configuration
kk.net	SPICE netlist for simulation
README.md	Documentation file (this file)


⸻

🧭 Steps to Simulate in eSim
	1.	Open eSim 2.5 → Load your project folder.
	2.	Open the schematic in KiCad Schematic Editor.
	3.	Go to Tools → Generate Netlist → Spice → Export Netlist.
	4.	Return to eSim and click Convert KiCad to Ngspice.
	5.	Choose Transient Analysis and run simulation.
	6.	Observe the output waveform and LED pulse behavior.


👨‍💻 Author

Harnoor Singh Khurana
Electronics Enthusiast | Circuit Designer | eSim Learner

