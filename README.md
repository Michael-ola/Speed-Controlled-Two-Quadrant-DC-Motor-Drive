# 🚀 Speed-Controlled Two-Quadrant DC Motor Drive

## 📌 Project Overview

This project implements a speed-controlled two-quadrant DC motor drive using MATLAB/Simulink. The model enables precise control over motor speed in both forward and reverse directions while allowing motoring and regenerative braking operations.

## 🎯 Objectives

- Develop and simulate a closed-loop control system for a two-quadrant DC motor drive.
- Implement speed and current controllers for stable operation.
- Analyze motor performance under various operating conditions.
- Visualize speed, current, voltage, and torque waveforms.

## ⚙️ Simulink Model Implementation

The Simulink model consists of key components such as:

- **Pulse Width Modulation (PWM) control**
- **Fully controlled bridge rectifier** with **six thyristors** for AC-DC conversion.
- **Speed and current controllers**
- **DC motor dynamics** based on electrical and mechanical equations
- **Pulse generator** that controls the **firing angle (alpha_deg)** of the thyristors.
- **Smoothing inductance** to reduce voltage ripple.
- **Visualization scopes** for speed, current, voltage, and torque.

## 🏷️ Methodology

## 🏎️ Speed Control Strategy

- A **Proportional-Integral (PI) speed controller** ensures precise speed regulation.
- A **current controller** maintains armature current within safe limits.
- A **Pulse Generator & Rectifier Bridge** control motor operation across two quadrants.

## 📊 Simulation Parameters

| Parameter                   | Value               |
| --------------------------- | ------------------- |
| Armature Resistance \(R_a\) | 0.5 Ω               |
| Armature Inductance \(L_a\) | 0.002 H             |
| Back EMF Constant \(K_b\)   | 0.8 V/rad/sec       |
| Load Inertia \(J\)          | 0.02 Kg.m²          |
| Damping Coefficient \(B\)   | 0.005 N.m/rad/sec   |
| Supply Voltage \(V\_{in}\)  | 220 V               |
| Speed Controller \(K_s\)    | Tuned PI Controller |
| Current Controller \(K_c\)  | Tuned PI Controller |

## 🏁 Simulation Scenarios

- **Acceleration Phase**: The motor starts from rest and accelerates to the reference speed.
- **Regeneration in Forward Direction**: When the reference speed decreases, the motor enters regenerative braking.
- **Reverse Operation**: The reference speed is set negative, reversing motor direction.
- **Regeneration in Reverse Direction**: The motor brakes while running in reverse.

## 🔄 Solver Configuration

- **Solver**: ode23tb (suitable for stiff electrical systems)
- **Simulation Time**: 0.1 seconds

## 🖥️ Results

The following results were obtained from the simulation:

- **Motor speed (`wm`,`wr`)**
- **Armature current (`ia`,`iar`)**
- **Voltages (`Vc`,`Va`)**
- **Firing angle (`alpha`)**
- **Electromagnetic torque (`Te`)**

## 📂 Repository Structure

```
🗂 Speed-Controlled-Two-Quadrant-DC-Motor-Drive
 ├── 🔬 Speed Controlled Two Quadrant DC Motor Drive.slx  # Simulink model
 ├── 📝 README.md   # Project documentation (this file)
```

## 🚀 How to Run the Simulation

1. **Clone the repository**:

```bash
git clone https://github.com/Michael-ola/Speed-Controlled-Two-Quadrant-DC-Motor-Drive.git
```

2. **Open MATLAB and navigate to the project folder.**
3. **Run the Simulink model**: Open `Speed Controlled Two Quadrant DC Motor Drive.slx` and click **Run**.
4. **View results**: Open Scope blocks to analyze speed, current, and voltage waveforms.

## 📌 Conclusion

This project successfully demonstrates a **closed-loop speed-controlled DC motor drive** operating in **two quadrants**, handling **forward/reverse motoring and regenerative braking**. The MATLAB/Simulink implementation provides a valuable tool for analyzing motor performance under different dynamic conditions.

---

## 🔧 Additional Technical Details

### **Fully Controlled Bridge Rectifier (6 Thyristors)**

- Converts **three-phase AC** into a **controllable DC voltage**.
- The **firing angle (alpha_deg)** determines the **DC output voltage level**, which in turn controls the motor speed.
- The **pulse generator** provides gating pulses to fire the thyristors at the appropriate angles.

### **Pulse Generator**

- Generates **gating signals** based on `alpha_deg`.
- Controls **when the thyristors turn on**, thus regulating the DC voltage output.

### **Smoothing Inductance**

- Filters out high-frequency ripples from the rectified DC voltage (`Vload`).
- Ensures a **smooth DC voltage** for the motor.

### **DC Motor Model**

- Receives the **controlled DC voltage (`Va`) from the rectifier**.
- Simulated using the **electromechanical transfer function**:
  1/(La.s + Ra) for electrical dynamics, and
  1/(J.s + Bt) for mechanical dynamics.
- The back EMF coefficient (`Kb`) influences the motor's response.
- Feedback mechanisms regulate motor speed (`wm`).

### **Angle and Torque Computation**

- The model computes the **firing angle** (`alpha`) by converting voltage signals (`Vc`) into degrees.
- The \*\*electromagnetic torque (`Te`) is derived from the motor's electrical and mechanical response.

## 📌 For any issues or contributions, feel free to open an **Issue** or a **Pull Request!** 🚀
