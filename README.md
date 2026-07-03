# Thermal Transport Analytics: Physics-Informed Thermal Conductivity Estimation

A data-driven thermal engineering project focused on estimating material thermal properties through sensor-based temperature acquisition, physics-informed modeling, and non-linear parameter estimation.

The project combines heat transfer, numerical optimization, experimental diagnostics, and transport phenomena to quantify thermal conductivity under realistic non-ideal conditions and evaluate the validity of conventional adiabatic assumptions.

---

# Executive Summary

Traditional thermal conductivity experiments assume:

- One-dimensional heat conduction
- Negligible radial heat loss
- Perfect insulation
- Adiabatic boundaries

While these assumptions simplify calculations, they rarely hold in real systems.

This project develops a thermal analytics framework using multi-sensor temperature acquisition and fin-theory modeling to investigate heat transport in a heated hollow copper rod.

By integrating experimental measurements, non-linear curve fitting, and convective heat-transfer correlations, the study quantifies radial heat leakage, validates fin-based thermal models, and demonstrates substantial deviations from classical conduction theory.

---

# Problem Statement

Can thermal conductivity be accurately estimated when significant radial heat loss exists?

How much error is introduced by the conventional adiabatic assumption?

Can fin-theory and convection-aware models better explain real thermal behavior?

---

# Objectives

- Estimate thermal conductivity of a hollow copper rod under steady-state conditions.
- Quantify conductive and convective heat transfer mechanisms.
- Evaluate the validity of one-dimensional conduction assumptions.
- Develop physics-informed thermal models using fin theory.
- Estimate unknown thermal parameters through non-linear regression.
- Measure and quantify radial heat leakage under realistic operating conditions.

---

# Experimental Setup

## Test Specimen

- Hollow Copper Rod
- Length: 180 mm
- Outer Diameter: 15 mm
- Inner Diameter: 14 mm

## Heating System

- DC Heater
- Voltage: 12 V
- Current: 0.5 A
- Heat Input: 6 W

## Instrumentation

- 5 K-Type Thermocouples
- Sensor Locations:
  - 60 mm
  - 90 mm
  - 120 mm
  - 150 mm
  - 180 mm

## Insulation

- Armaflex Closed-Cell Foam
- Thermal Conductivity:
  - 0.038 W/m·K

The setup generated five synchronized temperature streams used for thermal profile reconstruction and parameter estimation.

---

# Project Workflow

```text
Thermocouple Sensors
          │
          ▼
Temperature Acquisition
          │
          ▼
Steady-State Detection
          │
          ▼
Gradient Extraction
          │
          ▼
Thermal Model Selection
          │
          ▼
Non-Linear Curve Fitting
          │
          ▼
Parameter Estimation
          │
          ▼
Convective Analysis
          │
          ▼
Heat-Loss Quantification
```

---

# Thermal Modeling Framework

## Fourier Conduction Model

The initial analysis assumed:

- Steady-State Conditions
- One-Dimensional Heat Conduction
- No Radial Heat Loss

Using Fourier's Law:

```math
q = -kA \frac{dT}{dx}
```

Thermal conductivity was estimated directly from experimentally measured temperature gradients.

---

## Fin Theory Model

To account for distributed radial heat loss, the rod was modeled as a longitudinal fin.

The governing energy balance includes:

- Axial Conduction
- Natural Convection
- Distributed Heat Loss

Temperature distribution:

```math
T(x) = T_{\infty} + \theta_b
\frac{\cosh[m(L-x)]}{\cosh(mL)}
```

where:

- \(m\) = fin parameter
- \(L\) = rod length
- \(T_{\infty}\) = ambient temperature

The fin model provided a significantly better representation of observed temperature profiles.

---

# Data Analytics & Parameter Estimation

A non-linear Least Squares optimization framework was implemented to fit experimental temperature measurements against analytical fin-model solutions.

Estimated parameters included:

- Thermal Conductivity (k)
- Fin Parameter (m)
- Heat Transfer Coefficient (h)

The fitted model closely matched measured temperature distributions across all thermocouple locations.

---

# Convective Heat Transfer Analysis

To characterize radial heat loss mechanisms, natural convection correlations were incorporated.

## Dimensionless Numbers Evaluated

### Rayleigh Number (Ra)

Measures buoyancy-driven fluid motion.

```math
Ra = Gr \times Pr
```

### Nusselt Number (Nu)

Measures enhancement of heat transfer through convection relative to pure conduction.

```math
Nu = \frac{hL}{k}
```

## Correlation Used

### Churchill-Chu Natural Convection Correlation

Used to estimate realistic convective heat-transfer coefficients surrounding the insulated rod.

---

# Advanced Diagnostics

## Temperature Gradient Profiling

Computed:

```math
\frac{dT}{dx}
```

across all sensor locations.

Key Findings:

- Significant gradients persisted despite insulation.
- Heat transfer behavior deviated from ideal conduction assumptions.
- Distributed heat losses dominated thermal transport.

---

## Insulation Benchmarking

Multiple insulation materials were evaluated:

- Bare Rod
- Aluminum Foil
- Teflon Tape
- Rubber
- Armaflex

### Outcome

Armaflex exhibited the highest thermal retention and was selected for final experiments.

---

## Surface Temperature Monitoring

Additional sensors were placed on the insulation surface.

### Observation

Surface temperatures increased continuously throughout the experiment.

### Implication

This directly disproved the assumption that no heat escapes radially through the insulation.

---

# Results

## Thermal Performance

| Metric | Value |
|----------|----------|
| Heat Input | 6 W |
| Thermocouples | 5 |
| Steady-State Time | ~25 min |
| Final ΔT Stability | < 0.3°C |

---

## Radial Heat Loss

| Configuration | Radial Heat Loss |
|--------------|----------------|
| Bare Rod | 77% |
| Insulated Rod | 64% |

### Key Insight

Even with insulation, the majority of thermal energy was lost radially, highlighting the limitations of idealized laboratory assumptions.

---

## Model Validation

### Classical Assumption

❌ Pure Fourier conduction significantly overestimated thermal conductivity.

❌ Adiabatic boundary assumptions were invalid.

### Proposed Framework

✅ Fin-theory accurately captured observed temperature distributions.

✅ Convection-aware models provided realistic conductivity estimates.

✅ Experimental and fitted profiles showed strong agreement.

---

# Key Engineering Insights

### Insight 1

Thermal conductivity cannot be accurately estimated without accounting for distributed heat losses.

### Insight 2

Even high-performance insulation permits substantial radial energy leakage.

### Insight 3

Temperature-profile fitting is more reliable than direct gradient-based estimation.

### Insight 4

Real thermal systems require coupled conduction-convection analysis rather than simplified textbook assumptions.

---

# Technologies Used

## Programming & Analytics

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib

## Numerical Methods

- Non-Linear Least Squares Regression
- Curve Fitting
- Parameter Estimation
- Error Analysis

## Thermal Engineering

- Fourier Conduction
- Fin Theory
- Natural Convection
- Churchill-Chu Correlations
- Rayleigh Number Analysis
- Nusselt Number Analysis
- Heat Loss Modeling

---

# Impact

- Processed and analyzed 5 synchronized thermocouple data streams for thermal system identification.
- Developed a physics-informed parameter estimation framework using fin-theory and non-linear regression.
- Quantified 64–77% radial thermal power leakage under realistic operating conditions.
- Demonstrated the failure of conventional adiabatic assumptions widely used in thermal conductivity experiments.
- Re-engineered conductivity estimation equations using cylinder and convection corrections, reducing prediction errors to within 10%.
- Validated transport-phenomena models through experimental temperature-profile fitting and convective diagnostics.

---

# Key Learnings

- Thermal System Identification
- Experimental Heat Transfer
- Numerical Optimization
- Physics-Informed Modeling
- Convective Heat Transfer Analysis
- Sensor Data Analytics
- Parameter Estimation
- Engineering Model Validation

---

# Future Improvements

- Develop transient heat-transfer models.
- Integrate real-time thermal monitoring dashboards.
- Implement Bayesian parameter estimation techniques.
- Extend analysis to composite and non-metallic materials.
- Deploy automated thermal characterization workflows using IoT-enabled sensors.

---

## 👥 Contributors

* **Aman Agrawal** - [@Amanag185](https://github.com/Amanag185)
