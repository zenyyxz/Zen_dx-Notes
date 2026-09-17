---
title: Transistors & Operational Amplifiers Guide
subject: AL Physics
subtopic: Electronics
tags:
  - AL-Physics
  - Subtopic
  - Transistor
  - OpAmp
  - Gain
---

# 🎛️ Subtopic: Transistors & Operational Amplifiers Guide

> [!ABSTRACT] Core Focus
> BJT Common-Emitter characteristics, load line analysis, Op-Amp golden rules, and derivation of inverting and non-inverting amplifier gains.

---

## 1. Op-Amp Golden Rules

1. **Rule 1**: No current flows into either input terminal ($I_+ = I_- = 0$) because input impedance $R_{in} = \infty$.
2. **Rule 2**: Under negative feedback, the Op-Amp adjusts output to keep potential difference between input terminals zero ($V_+ = V_-$).

### Gain Derivations:

#### A. Inverting Amplifier:
Non-inverting input grounded ($V_+ = 0 \implies V_- = 0$ virtual ground).
$$I_{in} = rac{V_{in} - 0}{R_{in}} = rac{V_{in}}{R_{in}}$$
$$I_f = rac{0 - V_{out}}{R_f} = -rac{V_{out}}{R_f}$$
Since $I_{in} = I_f$:
$$rac{V_{in}}{R_{in}} = -rac{V_{out}}{R_f} \implies A_v = rac{V_{out}}{V_{in}} = -rac{R_f}{R_{in}}$$

#### B. Non-Inverting Amplifier:
$V_+ = V_{in} \implies V_- = V_{in}$.
$$I = rac{V_{in} - 0}{R_{in}} = rac{V_{out} - V_{in}}{R_f} \implies rac{V_{out}}{V_{in}} = 1 + rac{R_f}{R_{in}}$$