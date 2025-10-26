# 🔌 Basic PCB Projects

This repository showcases **three foundational PCB design projects** created using **KiCad**, focusing on analog and mixed-signal circuit design for beginners in electronics.  
Each project demonstrates schematic design, PCB layout, and practical circuit understanding.

---

## 📘 Projects Included

### 🟢 1. 5V Regulated Power Supply PCB

This project implements a **transformer-based 5V DC regulated power supply** designed using the **LM7805 voltage regulator IC**.  
It converts **230V AC mains** into a stable **5V DC output**, suitable for powering logic circuits, sensors, and microcontrollers.

**🔧 Circuit Overview**
- **AC Input:** The supply starts with a 230V AC input through a 230V–12V step-down transformer.  
- **Protection:** A fuse is added in series for overcurrent protection.  
- **Rectification:** A **full-wave bridge rectifier** is formed using four 1N4007 diodes (D1–D4) to convert AC to pulsating DC.  
- **Filtering:** A large **470µF capacitor (C1)** smoothens the rectified DC, while **0.1µF ceramic capacitors (C2, C3)** filter out high-frequency noise.  
- **Regulation:** The **LM7805** linear voltage regulator provides a constant 5V output even with small input fluctuations.  
- **Indication:** A **LED with a 150Ω resistor (R1)** indicates when the output is active.  

**🧠 Key Features**
- Converts 230V AC → 12V AC → 5V DC  
- Provides clean, regulated 5V output  
- Includes protection fuse and indicator LED  
- Built entirely with easily available through-hole components  

**📂 Files Included**
- `5V-Regulated-Power-Supply.kicad_sch` – KiCad schematic file  
- `5V-Regulated-Power-Supply.kicad_pcb` – PCB layout file  
- `5V-regulated-power-supply-schematic.png` – Circuit schematic  
- `pcb_layout.png` – PCB top view  
- `BOM.csv` – Bill of Materials  

**🧾 Bill of Materials**
| Component | Value / Type | Quantity | Description |
|------------|--------------|-----------|--------------|
| T1 | 230V/12V Step-down Transformer | 1 | Power isolation and voltage reduction |
| D1–D4 | 1N4007 | 4 | Rectifier diodes |
| C1 | 470µF / 25V | 1 | Filter capacitor |
| C2, C3 | 0.1µF | 2 | Noise filter capacitors |
| U1 | LM7805 | 1 | 5V voltage regulator |
| R1 | 150Ω | 1 | LED current limiter |
| D5 | LED (Red) | 1 | Power ON indicator |
| F1 | Fuse | 1 | Overcurrent protection |
| J1, J2 | Connectors | 2 | Input and output terminals |

**⚡ Applications**
- Embedded systems (Arduino, ESP32, microcontrollers)  
- Sensors and small electronic modules  
- Prototyping power source  

---

### 🟢 2. 555 Timer Astable Multivibrator PCB

This project demonstrates the use of the **NE555 timer IC** configured in **astable mode** to generate a continuous square wave output.  
The circuit is one of the simplest ways to produce a periodic ON/OFF signal used for LED blinking, clock pulses, or PWM control.

**🔧 Circuit Overview**
- The **555 timer (U2)** is wired in astable configuration — no external trigger is needed.  
- **R4** and **R5** form a resistor network that, along with **C3**, defines the frequency and duty cycle of the output waveform.  
- The **DIS** and **THR** pins work together to charge and discharge the timing capacitor (C3), continuously toggling the output.  
- **C4** is a small decoupling capacitor used to stabilize the control voltage and reduce noise.  
- An **LED (D2)** connected through **R6** visually indicates the output oscillation (blinking pattern).
- 
**→ Approximate frequency:** 720 Hz (LED blinks fast; values can be modified for slower blinking).

**🧠 Key Features**
- Generates a continuous square wave output  
- Adjustable frequency and duty cycle via resistors  
- LED output indicator  
- Simple, low-cost, and easy-to-solder PCB  

**📂 Files Included**
- `555-timer.kicad_sch` – Schematic design file  
- `555-timer.kicad_pcb` – PCB layout file  
- `555-timer-schematic.png` – Circuit diagram  
- `pcb_layout.png` – PCB layout image  
- `BOM.csv` – Bill of Materials  

**🧾 Bill of Materials**
| Component | Value / Type | Quantity | Description |
|------------|--------------|-----------|--------------|
| U2 | NE555P Timer IC | 1 | Generates pulse signal |
| R4 | 10kΩ | 1 | Timing resistor 1 |
| R5 | 10kΩ | 1 | Timing resistor 2 |
| R6 | 1kΩ | 1 | Current limiting resistor for LED |
| C3 | 0.1µF | 1 | Timing capacitor |
| C4 | 0.01µF | 1 | Control voltage stabilizer |
| D2 | LED | 1 | Output indicator |
| PWR_FLAG | — | 1 | Power supply indicator |

**⚡ Applications**
- LED blinkers  
- Clock pulse generation  
- Frequency modulation  
- Tone generation and PWM circuits  

---

### 🔵 3. BJT Astable Multivibrator
A **transistor-based astable multivibrator** that produces continuous oscillating output without using ICs — ideal for understanding the basic principles of transistor switching.

**🔧 Circuit Overview**
-The circuit consists of **two NPN transistors(2N3904)**, each driving an LED in its collector branch, and connected in a cross-coupled configuration using two **capacitors (220 µF each)** between the collector of each transistor and the base of the other.
-Two pairs of resistors control both the current through the LEDs (1 kΩ at each collector) and the charging rate of the capacitors (5 kΩ at each base).
-When one transistor turns on, it pulls its collector low and forward-biases the opposite transistor’s base through the coupling capacitor, turning it off.
-This alternating action creates a **continuous oscillation**: while one LED is ON, the other is OFF, and they toggle back and forth automatically.
-The entire circuit is powered by a single 3.7V power supply.

**Key Features**
- Built using two NPN transistors (2N3904)  
- Generates alternating ON/OFF states at both transistor outputs  
- Frequency depends on resistor and capacitor values  
- Demonstrates transistor biasing and feedback  

**Files Included**
- `BJT-Astable-Multivibrator.kicad_sch`-shematic design file 
- `BJT-Astable-Multivibrator.kicad_pcb`-PCB layout file
- `schematic.png`-Circuit diagram
- `pcb_layout.png`-PCB layout image  
- `BOM.csv`-Bill of materials

**🧾 Bill of Materials**
| Component | Value / Type | Quantity | Description |
|------------|--------------|-----------|--------------|
| Q1 ||Q2| 2N3904  NPN Transistors  | 2 | switching devices |
| R1 | 1kΩ | 1 | control the charging and discharging of capacitors and base currents of the transistors|
| R2 | 5kΩ | 1 | control the charging and discharging of capacitors and base currents of the transistors|
| R3 | 5kΩ | 1 | control the charging and discharging of capacitors and base currents of the transistors|
| R4 | 1kΩ | 1 | control the charging and discharging of capacitors and base currents of the transistors|
| C1 ||C2| 220uF | 2 | timing of the oscillation |
| D1 ||D2| LED | 2 | Output indicators |

**Applications**
- LED flasher  
- Pulse signal generator  
- Basic waveform demonstration circuit

---

## 🧰 Tools Used
- **KiCad 9.0** – Schematic capture and PCB layout

---

## 📁 Repository Structure
Basic-PCB-Projects/
┣ README.md
┣ 5V-Regulated-Power-Supply/
┣ 555-Astable-Multivibrator/
┗ BJT-Astable-Multivibrator/


## 🧠 Learnings
- Understood **schematic design principles** and **component selection**  
- Learned **PCB layout techniques**: track width, via placement, and routing order  
- Gained experience in **voltage regulation, oscillators, and transistor switching circuits**  
- Improved workflow in **KiCad file management and PCB documentation**

---

## ✍️ Author
**Niyathi Arun Kurthkoti**  
 ECE Student | Aspiring Embedded & PCB Design Engineer  
 
🔗 [LinkedIn](www.linkedin.com/in/niyathiarun)
