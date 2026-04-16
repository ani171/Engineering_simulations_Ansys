# ANSYS Thermal & Fluid Flow Simulation — CPU Cooling Analysis

> **Simulation of forced-convection heat dissipation in an electronics enclosure using ANSYS Icepak 2024 R2**

---

## Table of Contents

1. [Problem Statement](#problem-statement)
2. [Simulation Overview](#simulation-overview)
3. [Software & Environment](#software--environment)
4. [Model Components Summary](#model-components-summary)
5. [Step-by-Step Modelling Guide](#step-by-step-modelling-guide)
6. [Key Results Summary](#key-results-summary)
7. [Physics & Theory Reference](#physics--theory-reference)
8. [Parameter Reference Table](#parameter-reference-table)

## Problem Statement

Modern engineering systems require accurate and efficient modelling techniques to predict real-world behaviour before physical implementation. This project focuses on developing a simulation model in ANSYS Icepak to analyse thermal and fluid performance of a CPU cooling system under controlled operating conditions.

**The primary objectives are:**

- To design and simulate a forced-air cooling system for an electronics enclosure using ANSYS Icepak
- To apply realistic material properties (aluminium fins) and boundary conditions (fan flow rate, heat dissipation per chip)
- To evaluate system performance through velocity, temperature, and pressure simulation outputs
- To identify critical parameters affecting thermal management — including fin spacing, fan placement, and source power

The system models a compact electronics cabinet housing multiple heat-generating components (each dissipating **33 W**), cooled by three axial fans delivering a combined volumetric flow of **18 CFM**, exhausting through a rear opening. Aluminium fins are used as heat spreaders. The analysis is performed under **steady-state, turbulent, forced-convection** conditions.

## Simulation Overview

| Parameter | Value |
|---|---|
| Software | ANSYS Icepak 2024 R2 |
| Analysis Type | Steady-State Thermal + CFD |
| Flow Type | Forced Convection |
| Flow Regime | Turbulent (Re > 2000) |
| Turbulence Model | SST k-ω |
| Radiation | Ignored (dominated by forced convection) |
| Fan Flow Rate | 18 CFM (Volumetric) |
| Number of Fans | 3 (2D circular, y-offset 0.0775 m) |
| Heat Sources | 5 × 33 W = 165 W total |
| Fin Material | Aluminium (default) |
| Fin Thickness | 0.0025 m |
| Fin Count | 10 (y-offset 0.025 m spacing) |
| Mesh Type | Mesher-HD, Coarse |

## Software & Environment

- **ANSYS Icepak 2024 R2** — Electronics thermal simulation
- **Operating System:** Windows
- **Project File:** `Ainsath_Analysis`


## Model Components Summary

| Component | Type | Quantity | Key Parameter |
|---|---|---|---|
| Cabinet | Enclosure | 1 | Outer domain |
| Block (block.1) | Solid volume | 1 | PCB/chassis body |
| Opening (opening.1) | Exhaust vent | 1 | x = 0.006 m (after backing plate) |
| Fan (fan.1, fan.1.1, fan.1.2) | 2D Circular | 3 | 18 CFM, radius 0.01 m |
| Source (source.1 – source.2.4) | 2D Rectangle | 5 | 33 W each, y-z plane |
| Plate (plate.1 – plate.1.9) | Conducting thick | 10 | Aluminium, t = 0.0025 m |

## Step-by-Step Modelling Guide

---

### Step 1 — Domain Setup

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/ac1c5a4b-0982-4fde-b708-19dba94e93cd" />

*Initial domain boundary visible in the ANSYS Icepak viewport. The outer cube represents the computational domain. The coordinate axes (X, Y, Z) are shown at the bottom-left.*

**Key Notes:**
- The domain defines the outer boundary for the fluid region.
- The project tree on the left shows the standard structure: Problem setup, Solution settings, Groups, Post-processing, Points, Surfaces, Trash, Inactive, Model.
- Domain extents are set from the status bar: `min: -0.01/-0.01/-0.01`, `max: 1/1/1`.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/dd69c7b6-89a9-4d9e-9b70-63ba311b5330" />

*The domain is resized to closely enclose the cabinet. Reducing domain size improves mesh efficiency and solver performance.*

> **Theory:** The computational domain must be large enough to avoid boundary effects on the internal flow field, but not so large as to waste mesh elements in irrelevant regions.

### Step 2 — Cabinet (Enclosure) Creation

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/4ae452e3-76b6-4bc0-b087-bfdc24a62ac6" />


*The cabinet (labelled `block.1`) is created using the **Create blocks** option. Its 3D rectangular outline is now visible in the viewport. The properties panel on the right shows the geometry type as "solid" and the geom group as "From".*

**Cabinet dimensions (approximate from UI):**
- X: 0 → 0.875 m
- Y: 0 → 0.25 m
- Z: 0 → 0.356 m

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a70f9837-7935-4cac-8ed4-47646d0b8638" />


*The cabinet block is finalised. The block now represents the physical chassis/enclosure volume. Material loading is confirmed in the log panel at the bottom (`Please wait — loading material files`).*

> **Theory:** In Icepak, a **block** can represent a solid conducting body. The "solid" type means heat conduction is solved inside it — relevant for PCB substrates, heat spreaders, or structural walls.


### Step 3 — Block Creation (PCB/Chassis Volume)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/c633373e-1633-458d-9d13-a1a13ec951ff" />

*The inner block (PCB/chassis body) is positioned within the cabinet. The opening object (`opening.1`) is now also visible in the project tree, indicating the exhaust vent has been added.*

---

### Step 4 — Exhaust Opening

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/c633373e-1633-458d-9d13-a1a13ec951ff" />

*The exhaust opening is created using the **Create openings** option. It represents a free-flow boundary where air exits the enclosure. The opening is a rectangular plane type.*

> **Theory:** An **opening** in Icepak is a pressure boundary. It allows fluid to exit at ambient pressure (gauge = 0 Pa). This is the correct boundary condition for a vent or exhaust grille.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/04099cf1-a3cf-4868-98c0-ff91134a6ed1" />


*The opening is positioned along the x-axis starting at `x = 0.006 m` — immediately after the backing plate. The coordinate shown in the panel is: x-start = 0.006 m, ensuring the vent is on the downstream face of the enclosure.*

---

### Step 5 — Fan Modelling (2D)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/1abf7cce-7a89-4029-a44a-b04d6bbbb816" />


*Fans are modelled as **2D circular objects** (not 3D volumes). This simplification means they do not participate in meshing — reducing mesh complexity while still correctly applying the flow boundary condition.*

- Shape: **Circular**
- Model as: **2D** (no meshing participation)
- Location: `xC = 0.04 m`, `yC = 0.9475 m`
- Radius: `0.01 m` (inner), `0.01 m` (outer)

> **Theory:** A 2D fan in Icepak enforces a volumetric flow rate boundary condition across a planar disc. This is standard practice for electronics cooling where fans are represented by their performance curve rather than their blade geometry.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/14eed55c-207b-4e47-94d7-98d9c6d6565d" />


*The fan flow direction is set to **Positive**, flow type to **Volumetric**, and flow rate to **18 CFM (cubic feet per minute)**. The **Fixed** option is checked to enforce a constant flow rate regardless of system resistance.*

---

### Step 6 — Multiple Fans via Translate

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/4fb3fb32-60a1-44d0-96e2-44ffc20a54df" />


*To create two additional fans, the **Copy fan** dialog is used with the **Translate** operation. A `y-offset = 0.0775 m` is applied. This evenly spaces three fans across the inlet face of the enclosure.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/2219f97c-fd22-4b13-a8b2-6cd478620f11" />


*All three fans (`fan.1`, `fan.1.1`, `fan.1.2`) are now visible in the viewport and project tree, equally spaced along the y-direction.*

---

### Step 7 — Heat Sources

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/42f45a72-fa5e-4e15-a932-7ccaf59caec9" />

*Heat sources are created using **Create sources**. They represent power-dissipating electronic components (e.g., CPUs, GPUs) modelled as **invisible 2D rectangles** — no meshing, purely thermal boundary conditions.*

- Plane: **Y-Z** (x is kept at 0, no thickness)
- Shape: **Rectangular**
- Purpose: Maintain overall CPU temperature — not individual device analysis

> **Theory:** A 2D source in Icepak injects heat flux into the adjacent fluid/solid cells. Using 2D objects avoids the meshing overhead of resolving individual chip geometries, which is appropriate when the goal is system-level thermal management rather than per-component junction temperature.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/b3b23535-79a8-40c2-a0e2-fa759b7296b9" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/fe540d0d-54b0-41c4-90aa-9a0e6d45fc3c" />


*Each source is assigned a **Total power = 33 W**, set as constant. The thermal condition is "total power", which distributes heat uniformly across the source face.*

---

### Step 8 — Multiple Sources via Translate

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/bfed58ca-6345-4f63-be09-d9ed5334c8f7" />


*To create 4 additional sources (5 total), the copy/translate operation is used with `y-offset = 0.045 m`. This positions sources evenly across the y-span of the enclosure.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/50828d6f-10d1-41b7-b28b-e256a50bf1c7" />


*All five heat sources (`source.1`, `source.2`, `source.2.1` through `source.2.4`) are now visible as red rectangles in the viewport, distributed across the model.*

---

### Step 9 — Fin (Plate) Creation

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/5e649942-9f11-43ab-971a-eeda9be43035" />

*Fins are created using the **Create plates** option. A single aluminium fin plate (`plate.1`) is first defined in the y-z plane.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/7341f5d4-31a2-4fcf-adf9-58936c9194fe" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/48f1c2be-3619-41b9-a062-db02a286bc3f" />


*The fin (plate) properties are set:*
- *Thermal model: **Conducting thick***
- *Thickness: **0.0025 m***
- *Solid material: **default (Aluminium)***

> **Theory:** The **conducting thick** model solves the heat conduction equation through the fin thickness. Aluminium (k ≈ 202 W/m·K) is an excellent fin material due to its high thermal conductivity, low density, and machinability. Fins increase the effective surface area for convective heat transfer.

---

### Step 10 — Complete Fin Array

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/82318aaa-8b0b-4aca-96e9-efe3d895a4ff" />


*The initial fin is copied 9 times using the translate operation with `y-offset = 0.025 m` per copy, producing a total of **10 evenly spaced fins**.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/bfcae1a7-2528-402e-bd79-d4ade3bd62ea" />


*All 10 fins (`plate.1` through `plate.1.9`) are now visible as parallel orange plates. The fin array structure is clearly formed within the enclosure.*

---

### Step 11 — Model Verification

<br>

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/477c47f0-e2fc-45a4-81c5-c0a9e99d8015" />


*The completed model is viewed using **Model → Show objects by type**. All components are colour-coded by type: fins (plates) shown in orange. The model tree now contains all 21 objects.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/5d7b83da-3381-48c9-91f4-bf93ea4ee5ea" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/5deb1ebe-a868-43f8-8ef6-a755fb54606e" />

*The **Check model** tool confirms **no errors** found across all 21 objects. This verifies geometry integrity, object overlaps, and boundary condition completeness before meshing.*

---

### Step 12 — Mesh Generation

<br>

![Mesh Control — Settings](images/img_22.jpg)

*The **Mesh control** dialog is opened. Settings:*
- *Mesh type: **Mesher-HD***
- *Mesh units: mm*
- *Max element size: 15 (X), 12.5 (Y), 17.5 (Z)*
- *Mesh parameters: **Coarse***
- *Mesh assemblies separately: enabled*

> **Theory:** Mesher-HD generates a predominantly hex mesh which improves numerical accuracy and convergence speed. The coarse setting balances solution time versus accuracy for an initial analysis. Fin gaps and source surfaces automatically receive refined mesh.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/df4b1c31-7aa8-49ea-8925-9f771cd654e2" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/f0c7c6b1-1aed-4f10-8ae1-20d2c314b359" />

*Mesh generation is complete: **87,640 elements** and **92,388 nodes**. The mesh is displayed with cut-plane visualisation showing the structured hex mesh between fins. The log confirms mesh integrity checks passed.*

---

### Step 13 — Solution Settings

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/32a80770-d6c6-4d79-93e4-86ae6633fc9a" />

*The **Basic settings** dialog is configured:*
- *Number of iterations: **200***
- *Convergence criteria — Flow: **0.001**, Energy: **1e-7***

*The system also warns that Reynolds and Péclet numbers suggest turbulent flow — recommending the flow regime be set to "Turbulent".*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/2874fdfd-65f9-4a47-8eb8-81c948a52e53" />

*The **Problem setup wizard** is launched. Step 1 of 14 selects the physics to solve:*
- *✓ Solve for velocity and pressure*
- *✓ Solve for temperature*
- *☐ Solve for individual species (not required)*

---

### Step 14 — Flow Type — Forced Convection

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/abf0c056-35ea-4ea1-8b40-32729750b39a" />

*Step 2 of 14: **Flow has inertia (forced convection)** is selected. This is appropriate because fans actively drive the airflow — inertial forces dominate over buoyancy.*

> **Theory:** Forced convection is characterised by an externally driven flow (fan, pump). The governing parameter is the **Reynolds number (Re)**. When Re > 2000 (transition) or Re > 4000 (fully turbulent), turbulence models must be applied.

---

### Step 15 — Flow Regime — Turbulent

<br>

<img width="1600" height="860" alt="image" src="https://github.com/user-attachments/assets/6cd9867d-6708-43ed-b832-36bd6ddc7450" />

*Step 5 of 14: Flow regime is set to **Turbulent**. The ANSYS warning confirmed Re ≈ 11,922 and Péclet number ≈ 7,869 — well above the turbulent threshold of ~2,000.*

> **Theory:** The **Reynolds number** Re = ρVL/μ compares inertial to viscous forces. At Re > ~4,000 for internal flows, the flow is fully turbulent. Turbulence significantly enhances heat transfer compared to laminar flow (higher Nusselt numbers) but requires additional transport equations to model.

---

### Step 16 — Turbulence Model Selection

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/779a08ad-51f0-4c9a-b54d-0bd94b8974cc" />


*Step 6 of 14: The **SST k-ω (two-equation)** turbulence model is selected from the options: Zero equation, k-ε (two equations), RNG k-ε, Spalart-Allmaras, Enhanced k-ε, Realisable k-ε, SST k-ω.*

> **Theory:** The **SST (Shear Stress Transport) k-ω** model combines the k-ω model near walls (where it is accurate in adverse pressure gradients) with the k-ε model in the free stream (where k-ω is sensitive to free-stream conditions). It is the recommended model for internal cooling applications with separated flows and fin geometries.

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/f7b51c06-c710-4050-b80e-6f2c8e3bb678" />


*Step 7 of 14: **Ignore heat transfer due to radiation** is selected. Radiation can be neglected here because forced convection (with fans) dominates the heat transfer mechanism — a standard simplification for electronics cooling at moderate temperatures.*

---

### Step 17 — Radiation & Solar Load

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/726ece55-1067-4231-a809-9af1a5bfbdbf" />

*Step 9 of 14: Solar radiation is not included. This is appropriate for an indoor electronics enclosure application.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a78dc877-f74b-40a5-8360-d703a03e6081" />

*Step 10 of 14: **Variables do not vary with time (steady-state)** is selected. The system is assumed to have reached thermal equilibrium — appropriate for a continuously operating CPU at constant load.*

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/f00c89c7-88c7-4dbb-98b1-1c17ab8149fe" />

---



*Step 14 of 14: Altitude effects are not applied (sea-level operation assumed). Air properties (density, viscosity) are kept at standard conditions.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/ed26eef7-b0ea-4f57-9779-6e43e4c27997" />

### Step 18 — Steady-State Analysis

> **Theory:** **Steady-state analysis** solves the time-independent form of the Navier-Stokes and energy equations (∂/∂t = 0). This is valid when the thermal time constant of the system is much shorter than the time scale of load variations — typical for electronics operating at constant power.

---

### Step 19 — Solver Launch

<br>

*The **Solve** dialog is opened. Solution type is **New**. Solver options include: disable radiation, disable varying joule heating, use stabilised flow formulation, coupled pressure-velocity formulation. **Start solution** is clicked.*

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/e3f80282-a27a-46fd-8861-215b170f988e" />

---

### Step 20 — Solution Convergence

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/b00e0c0d-c8c7-4d1a-b042-2b93c65204df" />

*The **solution residuals** plot shows convergence of all variables (x-velocity, y-velocity, z-velocity, continuity, energy) over ~200 iterations. All residuals decrease monotonically, confirming a converged solution. The energy residual (white) reaches below 1×10⁻⁷ as set.*

---

### Step 21 — Post-Processing Setup

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/75ba2a4a-a961-4123-9cc1-cab7651e2e4b" />


*After the solution, **Plane cut** menu is selected to visualise results on a cross-sectional plane through the model.*

---

### Step 22 — Velocity Vector Plot

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/52dfc444-b1e1-4441-a9a0-11508390a9fc" />


*The **Plane cut vectors** dialog is configured to display **Velocity magnitude** vectors. Arrow style is set to **3D arrow**, calculated from "Local truths". The velocity vector field clearly shows air acceleration through the fin channels.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/7e96faa6-2500-45d2-96fb-ac3904cb9a2b" />


*The **velocity speed contour** on the cut plane shows:*
- *Maximum velocity: **~3.49 m/s** (in fin channels, shown in red/orange)*
- *Minimum velocity: **~0.00 m/s** (near walls)*
- *Flow is directed from fan inlet (right) through fin array to exhaust opening (left)*

> **Theory:** Velocity increases in narrow fin channels due to flow continuity (A₁V₁ = A₂V₂). Higher velocity enhances convective heat transfer coefficient h, which scales approximately as h ∝ V^0.8 for turbulent flow over surfaces.

---

### Step 23 — Temperature Contour Plot

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a7d95f9f-6c0a-4021-b02d-1d3589dca7c0" />

*The contour variable is switched to **Temperature**. The plane cut is positioned through the centre of the fin array (z = 0.509 m).*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/6e025cd6-514b-483d-a1de-1c9a9b1a94c0" />


*The **temperature contour** reveals the thermal gradient across the fin array:*
- *Maximum temperature: **~45.47 °C** (hottest fins, near heat sources — shown in red)*
- *Minimum temperature: **~20.00 °C** (inlet air temperature — shown in blue)*
- *Where fans blow cold air in, temperatures are lower — confirming effective cooling at fan inlet locations*

> **Theory:** The temperature distribution follows the **energy balance**: Q = ṁCp(T_out − T_in). Fins conduct heat from the source and dissipate it to the flowing air via convection. The temperature gradient from source to fin tip is governed by the **fin efficiency** η = tanh(mL)/(mL), where m = √(hP/kA).

---

### Step 24 — Pressure Distribution

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/b459c25d-eba9-4728-b6d4-60a7a35807a7" />


*The contour variable is changed to **Pressure** on the out-velocity plane cut.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/f4af5154-6eba-4290-9e5f-2cade0d1e699" />

*The **pressure contour** shows:*
- *Maximum pressure: **+1.17 N/m²** (upstream of fin array — fan pressure rise, shown in orange/red)*
- *Minimum pressure: **−7.09 N/m²** (downstream exhaust, shown in blue)*
- *The pressure drop across the fin array drives the flow*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/67f3d127-cda0-4515-8614-507b2282d206" />

*A closer view of the pressure distribution showing complex pressure variations between individual fins, including recirculation zones near fin edges.*

> **Theory:** **Pressure drop** across a fin heat sink is given by ΔP = f·(L/D_h)·(ρV²/2), where f is the friction factor, D_h is the hydraulic diameter of the fin channel, and V is the mean channel velocity. Fan operating point is the intersection of the fan curve and system curve.

---

### Step 25 — Object Face Mode — Source Temperatures

<br>

<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/fc4f7dec-a1d3-4883-9a8c-2a4dc7afe023" />

*In the Post menu, **Object face (node)** mode is selected to view results directly on object surfaces rather than on cut planes.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/7e61eb16-e13f-4179-b7f6-2e8f6454769d" />


*Selecting all heat sources in object face mode and displaying temperature shows each source's surface temperature. The sources reach **~53–59 °C**, consistent with 33 W dissipation per source under forced convection cooling.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/67fb0866-3119-4f0d-a81f-4fffbdf8da00" />

*Individual source temperatures are clearly visible as small coloured rectangles. Maximum source temperature is approximately **59 °C**, within safe operating limits for typical power electronics.*

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/0d6c7456-021f-4a75-9814-d303e1609a53" />

*An alternative model configuration (different component layout) shows a top-view temperature map. The fin array temperature range is **30.8 – 35.9 °C**, with the fan visible at the base. Hot spots correspond to source locations.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/0d43ed9a-ae6e-4ffc-a95b-3685e24522fa" />

*The **Solution overview** text output (Solve → Results) reports:*

```
Mass flow rates:
  cabinet_default_side_navy   Specified: 0 kg/s   Calculated: -0.00277667 kg/s
                               n/a                 Calculated:  0.00273787 kg/s

Below flow rates: n/a  -0.057000 m3/s / 0.0270040 m3/s

Fan operating points:
  delta_FF00012_2NENE   volume flow = 0.00706 m3/s, pressure rise = 1.6700 N/m2

Heat flows for objects with power specified (Calculated):
  S10 through S19: 7 W each (calculated)

Maximum temperatures:
  S10: 64.025°C, S11: 66.608°C, S12: 66.602°C, S13: 64.304°C ...
```

*This quantitative summary confirms energy balance and identifies the maximum junction temperatures across all sources.*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/573835ae-9d75-4a70-ae13-d235c70d4e0b" />

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/6f95f0c4-74db-4d44-aa32-ff272910419b" />


## Key Results Summary

| Metric | Value |
|---|---|
| Maximum source temperature | ~66 °C |
| Minimum air inlet temperature | 20 °C |
| Maximum fin temperature | ~45 °C |
| Maximum airflow velocity (fin channel) | ~3.5 – 12.6 m/s |
| System pressure drop | ~7 – 8.3 N/m² |
| Fan operating pressure rise | ~1.67 N/m² |
| Total heat load | 165 W (5 × 33 W) |
| Mass flow rate | ~0.00277 kg/s |

---

## Physics & Theory Reference

### Governing Equations

**Continuity (Mass Conservation):**
```
∂ρ/∂t + ∇·(ρV) = 0
```

**Momentum (Navier-Stokes):**
```
ρ(∂V/∂t + V·∇V) = -∇P + μ∇²V + ρg
```

**Energy:**
```
ρCp(∂T/∂t + V·∇T) = ∇·(k∇T) + Q̇
```

### Key Dimensionless Numbers

| Number | Formula | Significance |
|---|---|---|
| Reynolds (Re) | ρVL/μ | Laminar vs. turbulent; Re ≈ 11,922 here → turbulent |
| Nusselt (Nu) | hL/k | Convective vs. conductive heat transfer |
| Prandtl (Pr) | μCp/k | Momentum vs. thermal diffusivity of fluid |
| Péclet (Pe) | Re × Pr | Advection vs. diffusion; Pe ≈ 7,869 here |

### Fin Efficiency
```
η_fin = tanh(mL) / (mL)    where m = √(hP / kA_c)
```
- h = convective coefficient, P = fin perimeter, k = fin thermal conductivity, A_c = cross-sectional area

---

## Parameter Reference Table

| Object | Property | Value | Unit |
|---|---|---|---|
| Cabinet | Dimensions | 0.875 × 0.25 × 0.356 | m |
| Opening | x-start | 0.006 | m |
| Fan (each) | Flow rate | 18 | CFM |
| Fan | Radius | 0.01 | m |
| Fan spacing | y-offset | 0.0775 | m |
| Source (each) | Total power | 33 | W |
| Source spacing | y-offset | 0.045 | m |
| Fin | Thickness | 0.0025 | m |
| Fin spacing | y-offset | 0.025 | m |
| Fin count | — | 10 | — |
| Fin material | — | Aluminium | — |
| Mesh elements | — | 87,640 | — |
| Mesh nodes | — | 92,388 | — |
| Iterations | — | 200 | — |
| Flow convergence | — | 0.001 | — |
| Energy convergence | — | 1×10⁻⁷ | — |
