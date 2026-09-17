---
title: Errors & Measuring Instruments Guide
subject: AL Physics
subtopic: Measurements
tags:
  - AL-Physics
  - Subtopic
  - Errors
  - Vernier
  - Micrometer
  - Spherometer
---

# 📏 Subtopic: Errors & Measuring Instruments Guide

> [!ABSTRACT] Core Focus
> Systematic vs Random errors, Least Count formulas, zero error corrections, error propagation in calculations, Vernier Caliper, Micrometer Screw Gauge, and Spherometer practical procedures.

---

## 1. Least Count & Zero Errors

### Vernier Caliper:
$$\text{Least Count (LC)} = 1\text{ MSD} - 1\text{ VSD} = rac{1\text{ MSD}}{\text{Total Vernier Divisions}}$$
- **Positive Zero Error**: Vernier 0 is to the **right** of Main Scale 0 ($+$ correction subtracted from reading).
- **Negative Zero Error**: Vernier 0 is to the **left** of Main Scale 0 ($-$ correction added to reading).
- **Corrected Reading**: $\text{Corrected Reading} = \text{Observed Reading} - \text{Zero Error}$

### Micrometer Screw Gauge:
$$\text{Pitch} = rac{\text{Distance moved on main scale}}{\text{Number of full rotations}}$$
$$\text{Least Count (LC)} = rac{\text{Pitch}}{\text{Number of Head Scale Divisions (HSD)}}$$

### Spherometer:
Measures small thickness or radius of curvature $R$ of spherical surfaces:
$$R = rac{a^2}{6h} + rac{h}{2}$$
Where $a$ is the average distance between the 3 fixed legs and $h$ is the height measured by the central screw.

---

## 2. Error Propagation Formula Summary

| Operation | Equation | Absolute Error $\Delta Z$ / Fractional Error $rac{\Delta Z}{Z}$ |
| :--- | :--- | :--- |
| Sum | $Z = A + B$ | $\Delta Z = \Delta A + \Delta B$ |
| Difference | $Z = A - B$ | $\Delta Z = \Delta A + \Delta B$ |
| Product | $Z = A \cdot B$ | $rac{\Delta Z}{Z} = rac{\Delta A}{A} + rac{\Delta B}{B}$ |
| Quotient | $Z = A / B$ | $rac{\Delta Z}{Z} = rac{\Delta A}{A} + rac{\Delta B}{B}$ |
| Power | $Z = A^n \cdot B^m$ | $rac{\Delta Z}{Z} = n rac{\Delta A}{A} + m rac{\Delta B}{B}$ |