# Sliding-Mode-Controlled-DC-DC-Converter

This repository contains a Simulink model of a DC-DC converter regulated using a **Sliding Mode Controller (SMC)**. Sliding mode control is a robust, nonlinear control method that ensures fast dynamic response and high disturbance rejection, making it well-suited for power electronic converters in real-world applications like electric vehicles, renewable energy systems, and industrial power supplies.

---

## Model Description

The system models a bidirectional DC-DC converter controlled using an SMC-based duty cycle generator implemented as a MATLAB function block. The control law computes the duty cycle based on the real-time system states: input voltage (`Vin`), output voltage (`Vo`), inductor current (`il`), and output current (`io`). It incorporates converter parameters such as inductance (`L`) and capacitance (`C`) and uses control gains (`α₂/α₁` and `α₃/α₁`) to define and enforce the sliding surface.

---

## Control Function

The duty cycle `D` is calculated using:

```matlab
D = (Vo/Vin)
    - ((α₂/α₁) * (L/C) * il * Vin)
    + ((α₂/α₁) * (L/C) * io / Vin)
    - ((α₃/α₁) * (L/Vin) * (il + Vo));
