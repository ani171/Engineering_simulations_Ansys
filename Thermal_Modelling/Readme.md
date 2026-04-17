# ANSYS Icepak — PCB Thermal Simulation with Electronic Packages & Heat Sinks

> **Detailed thermal simulation of a PCB-mounted multi-package electronic system with forced-air cooling, heat sinks, and grille boundary — ANSYS Icepak 2021 R1**

---

## Table of Contents

1. [Problem Statement](#problem-statement)
2. [Project Objectives](#project-objectives)
3. [System Description & Assumptions](#system-description--assumptions)
4. [Simulation Overview Table](#simulation-overview-table)
5. [Model Components Summary](#model-components-summary)
6. [Step-by-Step Modelling Guide](#step-by-step-modelling-guide)
7. [Results Summary](#results-summary)
8. [Physics & Theory Reference](#physics--theory-reference)
9. [Input Parameters Reference Table](#input-parameters-reference-table)
10. [Observations & Conclusions](#observations--conclusions)

---

## Problem Statement

Based on the provided reference configuration, a detailed thermal simulation of an electronic system is performed using ANSYS Icepak. The goal is to analyse the thermal behaviour of a PCB mounted with multiple electronic packages, each fitted with a heat sink on the top side, under forced air cooling conditions within a system enclosure.

**The system models:**
- A PCB with 3–5 electronic packages 
- Individual heat sinks are attached to the top of each package
- Forced air cooling using up to 3 axial fans
- An enclosure with a grille on the inlet face
- Steady-state thermal analysis with ambient temperature of **20 °C**

**Design constraints applied:**

| Constraint | Value |
|---|---|
| Number of packages | 3–5 |
| Max power per device | ≤ 50 W |
| Max fan CFM | ≤ 100 CFM |
| Max fans | 3 |
| Ambient temperature | 20 °C |
| Heatsink | 1 per device (detailed fin type) |
| Grille | Present on inlet face |

---

## Project Objectives

- To design and simulate a PCB-level electronics cooling system using ANSYS Icepak
- To model detailed semiconductor packages (QFP, PBGA) with accurate die, substrate, and solder layer properties from the package library
- To attach and configure extruded aluminium heat sinks on each package
- To apply forced-convection cooling via three axial fans drawing air through the enclosure
- To characterise thermal performance: temperature distribution, velocity field, and pressure distribution
- To determine the junction temperature of each device and the heat sink thermal resistance (θ_sa)
- To identify critical parameters affecting package temperatures and propose optimisation strategies

---

## System Description & Assumptions

### Physical Configuration
- **Enclosure:** Rectangular cabinet (0.4 m × 0.13 m × 0.25 m)
- **PCB:** Single compact PCB (0.4 m × 0.25 m), 1.6 mm thick, FR-4 substrate with 3 copper trace layers
- **Packages:** 1 × PBGA (700-BGA, 51 mm, 12 W die) + 3 × QFP (184-lead, 32 mm, 8 W die each)
- **Heat sinks:** Detailed extruded fin type, 5 fins, 0.005 m thick, aluminium (default)
- **Fans:** 3 × 2D circular fans, Y-Z plane, intake type, 20 CFM each, fixed volumetric flow
- **Inlet boundary:** Grille on the Min-X cabinet face (default open grille)
- **Outlet:** Default cabinet openings allow air exhaust

### Assumptions
- Steady-state analysis (thermal equilibrium assumed)
- Ambient air temperature = 20 °C at sea level
- Radiation heat transfer is ignored — forced convection dominates
- PCB modelled as compact (homogenised thermal conductivity, no individual component placement)
- Fan flow is normal to the Y-Z plane, direction positive (into domain)
- Die materials are Si-Typical; die pad is Pad_material; die attach is Die_attach_material
- Joule heating convergence criterion = 1×10⁻⁷

---

## Simulation Overview Table

| Parameter | Value |
|---|---|
| Software | ANSYS Icepak 2021 R1 |
| Project name | Anirudh_Prasad_Final_Project |
| Analysis type | Steady-state thermal + CFD |
| Flow type | Forced convection (inlet/outlet) |
| Flow regime | Turbulent (Re ≈ 42,143; Pe ≈ 29,858) |
| Turbulence model | Zero equation (mixing length) |
| Radiation | Ignored |
| Ambient temperature | 20 °C |
| Fan type | 2D circular, intake |
| Fan flow (each) | 20 CFM |
| Fan count | 3 (Fan_1, Fan_2, Fan_3) |
| Fan location | Y-Z plane, x = 0.4 m |
| Total system power | 36 W (PBGA 12 W + 3×QFP 8 W) |
| PCB | FR-4, 1.6 mm thick, 3 Cu trace layers |
| Mesh type | Mesher-HD, Normal |
| Mesh elements | 213,689 (refined) / 190,210 (initial) |
| Mesh nodes | 224,534 / 200,274 |
| Iterations | 200 |
| Flow convergence | 0.001 |
| Energy convergence | 1×10⁻⁷ |

---

## Model Components Summary

| Component | Type | Quantity | Key Specification |
|---|---|---|---|
| Cabinet | Enclosure | 1 | 0.4 × 0.13 × 0.25 m, Min-X = Grille |
| PCB.1 / PCB_1 | Compact PCB | 1 | FR-4, 1.6 mm, 3 Cu layers |
| PBGA | Package (BGA) | 1 | 700-BGA, 51 mm, 12 W, Si die 15.3×15.3 mm |
| QFP_1, QFP_2, QFP_3 | Package (QFP) | 3 | 184-lead, 32 mm, 8 W each, Si die 9.6×9.6 mm |
| HS_PBGA | Heat sink (detailed) | 1 | Extruded, 5 fins, X-direction flow |
| HS_QFP_1/2/3 | Heat sink (detailed) | 3 | Extruded, 5 fins, X-direction flow |
| Fan_1, Fan_2, Fan_3 | 2D Circular fan | 3 | 60 CFM each, intake, Y-Z plane |

---

## Step-by-Step Modelling Guide

---

### Step 1 — Cabinet & Enclosure Setup

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/3fe25eb5-03c0-4924-9179-ae9f2b61d889" />

*The cabinet (enclosure) is created as a **Prism** geometry type. Dimensions confirmed from the properties panel:*
- *x: 0 → 0.4 m*
- *y: 0 → 0.13 m*
- *z: 0 → 0.25 m*

*This defines the fluid domain boundary. The coordinate system is shown in the viewport — X is the streamwise direction (fan inlet to outlet).*

> **Theory:** The enclosure bounds the computational domain. All internal objects (PCB, packages, fans, heat sinks) must lie within this volume. The cabinet faces can be set as walls, openings, grilles, or fans depending on the physical boundary condition.

---

### Step 2 — Fan Placement (2D Circular)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/c20739f4-e4dd-41d6-90cf-ceb7dc3fc42d" />


*The first fan (`Fan_1`) is placed as a 2D circular object on the **Y-Z plane** at x = 0.4 m (the downstream face of the enclosure):*
- *Type: **2-D**, Geom: **Circular***
- *Radius: 0.025 m, Inner radius: 0.02 m*
- *Centre: xC = 0.4 m, yC = 0.07 m, zC = 0.05 m*

> **Theory:** A 2D fan in Icepak imposes a volumetric flow boundary condition across a planar disc without requiring 3D blade geometry. The annular gap (inner/outer radius) represents the real fan blade swept area.

---

### Step 3 — Fan Properties — Intake, 60 CFM

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/f67e3e6e-0211-42a2-8e0a-1a4a537e643b" />

*All three fans are configured with identical properties via the multi-select **Fans [*multiple*]** dialog:*

| Setting | Value |
|---|---|
| Fan type | **Intake** |
| Flow direction | Normal, Positive |
| Flow type | **Fixed** |
| Volumetric flow | **60 CFM** |
| Total temperature | Ambient |
| Gauge pressure | 0 N/m² |

*Intake type means fans draw air into the domain from the Min-X grille face — the correct configuration for side-intake cooling.*

> **Theory:** An intake fan enforces a specified volumetric inflow. The **fixed flow** setting holds flow rate constant regardless of system back-pressure. Total temperature at ambient (20 °C) sets the incoming air temperature boundary condition.

---

### Step 4 — Cabinet Wall Type — Grille on Min-X Face

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/304087d2-8a2b-478b-92d4-6a25c2e9c50d" />


*The **Cabinet [cabinet.1]** properties panel shows the wall type assignment for each face:*
- *Min X: **Grille** (inlet face — allows air entry through perforated grille)*
- *All other faces: **Default** (solid wall, no-slip boundary)*

*The 3D viewport confirms the model with the grille face (hatched pattern, top-left in the isometric view) and three fans on the opposite face.*

> **Theory:** A **grille** boundary in Icepak models a perforated wall with a specified open area ratio and pressure loss coefficient. It allows flow through while accounting for flow restriction — more physically accurate than a fully open boundary for real enclosure inlets.

---

### Step 5 — PCB Creation (Compact Type)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/1ee04ae8-2363-42e1-81c6-f30e697eb302" />

*The PCB properties dialog for `pcb.1` shows:*
- *PCB type: **Compact***
- *Substrate thickness: **1.6 mm***
- *Substrate material: **FR-4***
- *Number in rack: 1, Rack spacing: 0.2 m*
- *Total power: 0 W (PCB itself is passive — power only in packages)*
- *Trace layer type: **Detailed** — 3 copper trace layers defined*

**Trace layer configuration:**

| Layer | Thickness | % Coverage | Material |
|---|---|---|---|
| 1 | 2 Cu-oz/ft² | 50% | Cu-Pure |
| 2 | 1.5 Cu-oz/ft² | 80% | Cu-Pure |
| 3 | 2 Cu-oz/ft² | 30% | Cu-Pure |

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a6db6516-c933-438c-be65-60b0e34b0ca9" />

*Computed effective conductivities:*
- *In-plane (plane): **23.4301 W/m·K***
- *Through-thickness (normal): **0.3963 W/m·K***

> **Theory:** The **compact PCB model** homogenises the layered PCB structure into an effective anisotropic thermal conductivity. The in-plane conductivity is much higher than through-thickness because the copper traces run horizontally — heat spreads laterally in the plane of the board and conducts poorly through the FR-4 dielectric in the vertical direction. Detailed trace specification computes these values from copper weight, coverage, and material properties.

---

### Step 6 — Package Library Search — QFP (184-Lead, 32 mm)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/37dcf179-43f9-4f4c-9957-ee70047a1a13" />

*The **Search package library** dialog is used to find a suitable QFP package. Criteria set:*
- *Package type: **QFP***
- *Min dimension: 1 mm, Max dimension: 100 mm*

*The selected package: **184_Lead_PQFP_32mm** — Size: 32 mm, Balls/Leads: 184*

> **Theory:** **QFP (Quad Flat Package)** is a surface-mount IC package with leads on all four sides. The 184-lead 32 mm PQFP is a common size for mid-complexity FPGAs, ASICs, and DSP chips. The package library contains pre-defined geometry and material layup based on JEDEC standards.

---

### Step 7 — PCB with QFP Packages Placed (Top View)

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/4be33afc-1345-4750-8b2e-6141a1455e9b" />

*Three QFP packages (`184_Lead_PQFP_32mmX32mm`, `.2`, `.3`) are placed on the PCB. The view confirms:*
- *Package positions distributed across the PCB*
- *PCB_1 at y = 1.6 mm (substrate thickness offset)*
- *Viewport dimensions confirm PCB extent: x = 0 → 0.4 m, z = 0 → 0.25 m*

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/a5e95117-d075-47fc-8107-248d4c26df0b" />

*Top-down schematic view of the full system. All three QFP packages (`184_Lead_PQFP_32mmX32mm`, `.2`, `.3`) are visible on the PCB, each horizontally aligned with one of the three fans (`Fan_1`, `Fan_2`, `Fan_3`) on the right face. This alignment ensures each fan provides direct cooling airflow over its corresponding package.*

---

### Step 8 — PBGA Package Library Search

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/d38d5a7f-cf30-4a2a-8cf9-f9e28b35bf61" />

*The **Search package library** dialog for PBGA (Plastic Ball Grid Array):*
- *Package type: **PBGA***
- *Selected: **700_BGA_40X40_5perip** — Size: 51 mm, Balls/Leads: 40, Pitch: 1.27 mm*

> **Theory:** **PBGA (Plastic Ball Grid Array)** uses solder balls on the underside for mounting. BGAs allow more I/O connections than QFP for the same package footprint and offer better thermal performance through the solder ball array. The 51 mm package represents a large processor or FPGA die.

---

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/4f340d54-4db2-43ec-acdc-d88787bf25db" />

### Step 9 — Full Model with PBGA and All Heat Sinks

<br>

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/1f4fe00e-fe9b-47b5-9d0d-0943132cbcc1" />

*Upper image: All packages placed — **PBGA** (top-left), **QFP_1**, **QFP_2**, **QFP_3** — with all four heat sinks (green wire frames) and three fans visible. The PBGA heat sink (`HS_PBGA`) is larger due to the higher 12 W power dissipation.*

*Lower image: **HS_PBGA** heat sink detail dialog:*
- *Type: **Detailed**, Flow direction: **X***
- *Fin type: **Extruded***
- *Fin spec: Count/thickness — Count: **5**, Thickness: **0.005 m***
- *Offset: 0.0 m in both directions*
- *Coordinates: xS = 0.05 m, yS = 3.75 mm, yA = 0 m, zS = 0.1 m, zL = 0.051 m*

> **Theory:** **Extruded aluminium heat sinks** are characterised by the number of fins, fin thickness, fin height, and base thickness. Heat spreads from the die through the package substrate into the heat sink base, then conducts up the fin height and convects to the airflow. The fin count and fin spacing (gap = (W - n·t)/(n-1)) determine both thermal resistance and pressure drop.

---

### Step 11 — QFP Die/Mold Properties — 8 W Silicon Die

<br>

![QFP_3 Die/Mold settings — 8W, Si die 9.6×9.6 mm](images/img_12.jpg)

*The **Die/Mold** tab for `QFP_3` shows the detailed die stack:*

**Die settings:**
| Property | Value |
|---|---|
| Material | Si-Typical |
| Size | 9.6 mm × 9.6 mm |
| Thickness | 0.64 mm |
| Total power | **8 W** (constant) |

**Die pad:**
| Property | Value |
|---|---|
| Material | Pad_material |
| Size | 12.8 mm × 12.8 mm |
| Thickness | 0.1 mm |

**Die attach:**
| Property | Value |
|---|---|
| Material | Die_attach_material |
| Thickness | 0.05 mm |

> **Theory:** The die stack thermal resistance path is: Die → Die attach → Die pad → Package substrate → Solder → PCB. Each layer contributes a conduction resistance R = t/(k·A). The **die attach** layer (typically silver-filled epoxy or solder, k ≈ 3–30 W/m·K) is often the most critical resistance in the stack due to its low conductivity relative to silicon (k ≈ 148 W/m·K).

---

### Step 12 — PBGA Die/Mold Properties — 12 W Silicon Die

<br>

![PBGA Die/Mold settings — 12W, Si die 15.3×15.3 mm](images/img_13.jpg)

*The **Die/Mold** tab for the PBGA package shows:*

**Die settings:**
| Property | Value |
|---|---|
| Material | Si-Typical |
| Size | 15.3 mm × 15.3 mm |
| Thickness | 0.35 mm |
| Total power | **12 W** (constant) |

**Die pad:**
| Property | Value |
|---|---|
| Material | Pad_material |
| Size | 20.4 mm × 20.4 mm |
| Thickness | 0.1 mm |

**Die attach:**
| Property | Value |
|---|---|
| Material | Die_attach_material |
| Thickness | **0.04 mm** |

*The PBGA die is larger (15.3 mm vs 9.6 mm for QFP) and dissipates more power (12 W vs 8 W), making it thermally more challenging and justifying a larger heat sink.*

---

### Step 13 — Mesh Generation — 190,210 Elements

<br>

![Mesh control dialog — Normal, Mesher-HD](images/img_14.jpg)

*The **Mesh control** panel confirms a successfully generated mesh:*
- *Num elements: **190,210**, Num nodes: **200,274***
- *Mesh type: **Mesher-HD**, Mesh units: m*
- *Max element size: X = 0.02 m, Y = 0.0065 m, Z = 0.0125 m*
- *Minimum gap: X = 0.00096 m, Y = 3.5×10⁻⁵ m, Z = 0.0005 m*
- *Mesh parameters: **Normal***
- *Min elements in gap: 3, Min elements on edge: 2, Max size ratio: 2*
- *✓ Mesh assemblies separately (each package meshed independently)*

> **Theory:** **Mesher-HD** generates predominantly hexahedral elements aligned with the Cartesian coordinate system. **Normal** density balances solution accuracy with computational cost. The minimum gap constraint in Y (3.5×10⁻⁵ m) ensures at least 3 elements resolve the thin die attach and PCB trace layers, which are critical for accurate junction temperature prediction.

---

### Step 14 — Mesh Display & Cut-Plane View

<br>

![Mesh display — cut-plane through model](images/img_15.jpg)

*Upper image: The **Mesh control Display tab** shows the mesh visualised as a cut-plane (Volume/Cut plane mode). The mesh is visible through the enclosure, showing structured hex elements with refinement around the packages and heat sinks.*

*Lower image: 2D cut-plane view looking down the Y-axis. All three fans (left column), three QFP packages (centre), and the PBGA (right of QFP_2) are visible. The mesh refinement around each package body is clearly visible — finer elements near die surfaces, coarser in the open air volume.*

---

### Step 15 — Mesh Quality — Face Alignment

<br>

![Mesh quality — face alignment histogram](images/img_16.jpg)

*The **Quality → Face alignment** histogram for the 213,689-element mesh shows:*
- *Min alignment: **0.282393**, Max: **1.0***
- *The vast majority of elements (>160,000) score at or near 1.0 — indicating excellent orthogonality*
- *Very few elements below 0.5 — no severely distorted elements (threshold < 0.05)*

> **Theory:** **Face alignment** measures how orthogonal the mesh face normals are to the cell-to-cell connection vectors. A value of 1.0 is perfect alignment (pure hex cell). Values below 0.05 indicate severe distortion that can cause numerical errors. This mesh quality is excellent for electronics thermal simulation.

---

### Step 16 — Mesh Quality — Skewness

<br>

![Mesh quality — skewness histogram](images/img_17.jpg)

*The **Quality → Skewness** histogram shows:*
- *Min skewness: **0.0**, Max: **1.0***
- *Peak concentration at 1.0 — majority of elements are near-perfect (skewness = 1 means zero skew in Icepak's convention)*
- *Only a small number of elements at 0.4–0.5 range — corresponding to transition regions near package edges*

> **Theory:** **Skewness** quantifies how far a cell deviates from an ideal shape. In Icepak's convention, skewness = 1.0 is ideal. Low skewness values indicate distorted cells that can reduce solver accuracy and slow convergence. The predominantly high skewness scores confirm mesh quality is acceptable for this simulation.

---

### Step 17 — Solution Settings & Convergence Criteria

<br>

![Basic settings — 200 iterations, convergence criteria](images/img_18.jpg)

*The **Basic settings** dialog and mesh display confirm:*

| Setting | Value |
|---|---|
| Number of iterations | **200** |
| Flow convergence | **0.001** |
| Energy convergence | **1×10⁻⁷** |
| Joule heating | **1×10⁻⁷** |

*The log panel shows the ANSYS warning: **"Approximate Reynolds number = 42,143 and Péclet number = 29,858.6 — Turbulent flow regime recommended."** This confirms the flow is well into the turbulent regime.*

---

### Step 18 — Solution Settings & Convergence Criteria (continued)

<br>

![Problem setup wizard — forced convection and turbulent](images/img_19.jpg)

*Step 2 of 14: **Flow has inlet/outlet (forced convection)** selected — appropriate because fans create inertia-driven flow.*

*Step 5 of 14: **Set flow regime to turbulent** selected — justified by Re = 42,143 >> 4,000 threshold for fully turbulent flow.*

---

### Step 19 — Turbulence Model & Radiation Settings

<br>

![Turbulence — Zero equation; Radiation — ignored](images/img_20.jpg)

*Step 6 of 14: **Zero equation (mixing length)** turbulence model selected. This algebraic model is the simplest available in Icepak and is suitable for electronics cooling problems with well-defined flow channels.*

*Step 7 of 14: **Ignore heat transfer due to radiation** — radiation neglected because forced convection heat transfer coefficient is orders of magnitude larger than radiation at these temperatures.*

> **Theory:** The **zero-equation (mixing length) model** assumes turbulent viscosity is proportional to a local length scale (the mixing length). It requires no additional transport equations — making it computationally cheap. It is adequate for moderate-complexity electronics enclosures where flow paths are well-defined by the geometry. For separated flows or recirculation zones, higher-order models (k-ε, SST k-ω) provide better accuracy.

---

### Step 20 — Power & Temperature Limit Summary

<br>

![Power and temperature limit setup — all device powers confirmed](images/img_21.jpg)

*The **Power and temperature limit setup** dialog provides a consolidated view of all power-dissipating objects:*

| Object | Power (W) |
|---|---|
| HS_QFP_1 | — (passive) |
| HS_QFP_3 | — (passive) |
| HS_QPF_2 | — (passive) |
| **PBGA** | **12** |
| PCB.1 | 0 |
| **QFP_1** | **8** |
| **QFP_2** | **8** |
| **QFP_3** | **8** |
| **Total power** | **36 W** |

*Default temperature limit: **20 °C** (ambient)*

---

### Step 21 — Solution Convergence Residuals

<br>

![Solution residuals — Anirudh_Prasad_Final_Project01](images/img_22.jpg)

*The solution residuals plot for **Anirudh_Prasad_Final_Project01** over 200 iterations:*
- *All velocity components (x, y, z) converge to ~1×10⁻⁵*
- *Continuity residual (yellow) decreases but plateaus at ~3×10⁻⁴ — still acceptable for engineering analysis*
- *Energy residual (white) drops sharply below 1×10⁻¹⁰ at iteration ~200 — confirming energy equation is fully converged*

*The monotonic decrease of all residuals without oscillation confirms a stable, well-posed solution.*

---

### Step 22 — PCB Temperature & PBGA Temperature Contours

<br>

![PCB temperature contour](images/img_23.jpg)

**PCB Temperature (upper image):**

*The PCB surface temperature contour shows:*
- *Maximum: **~35.8 °C** (near PBGA package, hottest component — shown in green/yellow)*
- *Minimum: **~20.8 °C** (inlet side near fans — shown in dark blue)*
- *The PBGA is the dominant thermal load and creates the highest PCB surface temperature*
- *QFP packages (QFP_1, QFP_2, QFP_3) are visible as distinct warm regions*

**PBGA Temperature (lower image):**

*Temperature distribution on the PBGA package:*
- *Maximum die temperature: **~85.9 °C** (package junction — shown in red)*
- *Minimum: **~27.3 °C** (heat sink fin tips — shown in blue)*
- *The hot spot is concentrated at the die centre — typical for power-dense BGA packages*
- *The heat sink significantly reduces temperatures from die to fin tip*

> **Theory:** **Junction temperature T_j** is the temperature at the die–package interface. It determines device reliability — semiconductor manufacturers specify maximum T_j (typically 85–125 °C for commercial grade, 125–150 °C for industrial grade). The simulation confirms T_j = 85.9 °C for PBGA — within safe range for a 12 W device.

---

### Step 23 — QFP Temperature & Velocity Vector Field

<br>

![QFP temperature contour and velocity vectors](images/img_24.jpg)

**QFP Temperature (upper image):**

*Temperature on the QFP packages:*
- *Maximum: **~44.5 °C** (QFP_1 junction — closest to PBGA, shown in red)*
- *Minimum: **~23.6 °C** (heat sink fin tips)*
- *QFP packages run significantly cooler than the PBGA (44.5 °C vs 85.9 °C) due to lower 8 W power*

**Velocity Vector Field (lower image):**

*3D velocity vector plot inside the enclosure:*
- *Maximum velocity: **~10.33 m/s** (fan discharge jet — shown in red/orange)*
- *Minimum: **0.00 m/s** (near walls)*
- *Flow enters from fans (right), travels as a parallel jet across the PCB surface, and exits through the grille (left)*
- *Heat sinks (green wire frames) visibly deflect and accelerate the flow through their fin channels*
- *Recirculation visible near the far corners of the enclosure — expected in a confined cavity*

> **Theory:** Air velocity over the packages determines the convective heat transfer coefficient h. For turbulent flow over heat sink fins, h scales as **h ∝ V^0.8·Pr^0.33·k/D_h** (Dittus-Boelter correlation). The 10.33 m/s jet velocity near the fans is sufficient to maintain the QFP packages at safe temperatures despite the confined geometry.

---

### Step 24 — Pressure Distribution at QFPs and PBGA

<br>

![Pressure at QFPs and PBGA — plane cuts](images/img_25.jpg)

**Pressure at QFPs (upper image):**

*Pressure contour on a Y-plane cut through the QFP packages:*
- *Maximum: **+2.67 N/m²** (upstream of heat sinks — fan stagnation pressure, shown in red)*
- *Minimum: **−24.32 N/m²** (downstream / grille side, shown in blue)*
- *Total pressure drop across the system: ~27 N/m²*
- *Sharp pressure gradient visible across the heat sink fin array — confirms fins are the primary flow restriction*

**Pressure at PBGA (lower image):**

*Pressure contour on a Y-plane through the PBGA:*
- *Maximum: **+3.64 N/m²** (stagnation at PBGA heat sink leading edge)*
- *Minimum: **−2.91 N/m²** (recirculation zone behind heat sink)*
- *Lower overall pressure magnitude — PBGA heat sink is positioned with different flow approach angle*

> **Theory:** **System pressure drop** ΔP must be matched by the fan operating point. Fans have a characteristic P-Q curve; the system operating point is where the fan curve intersects the system resistance curve. Higher ΔP with the same fan CFM means less cooling. The ~27 N/m² total ΔP is well within the typical operating range of 20 CFM axial fans.

---

## Results Summary

### Temperature Summary

| Device | Package Type | Power (W) | Max Temp (°C) | Min Temp (°C) | ΔT above ambient |
|---|---|---|---|---|---|
| PBGA | BGA 51 mm | 12 | **85.9** | 27.3 | 65.9 |
| QFP_1 | QFP 32 mm | 8 | **44.5** | 23.6 | 24.5 |
| QFP_2 | QFP 32 mm | 8 | ~42 | 23.6 | ~22 |
| QFP_3 | QFP 32 mm | 8 | ~42 | 23.6 | ~22 |
| PCB surface | FR-4 compact | 0 | **35.8** | 20.8 | 15.8 |

### Flow & Pressure Summary

| Metric | Value |
|---|---|
| Maximum air velocity | 10.33 m/s |
| Total system pressure drop | ~27 N/m² |
| Fan inlet pressure (PBGA zone) | +3.64 N/m² |
| Fan discharge zone velocity | ~10 m/s |
| Ambient temperature | 20 °C |

### Mesh Quality Summary

| Metric | Value |
|---|---|
| Total elements | 213,689 |
| Total nodes | 224,534 |
| Min face alignment | 0.282 |
| Max face alignment | 1.0 |
| Dominant skewness | ~1.0 (excellent) |

---

## Physics & Theory Reference

### Governing Equations

**Continuity:**
```
∇·(ρV) = 0
```

**Momentum (Navier-Stokes, steady-state):**
```
ρ(V·∇V) = -∇P + μ_eff·∇²V
```

**Energy:**
```
ρCp(V·∇T) = ∇·(k∇T) + Q̇_vol
```

**Zero-Equation Turbulence (mixing length):**
```
μ_t = ρ · l_m² · |∂u/∂y|    where l_m = mixing length
μ_eff = μ_lam + μ_t
```

### Key Dimensionless Numbers

| Number | Value (this simulation) | Significance |
|---|---|---|
| Reynolds (Re) | **42,143** | Strongly turbulent (>>4,000) |
| Péclet (Pe) | **29,858** | Advection >> diffusion |
| Prandtl (Pr) | ~0.71 (air) | Thermal ≈ momentum diffusivity |

### Thermal Resistance Network

The package junction-to-ambient thermal resistance:

```
θ_ja = θ_jc + θ_cs + θ_sa

where:
  θ_jc = junction-to-case (die + die attach + substrate)
  θ_cs = case-to-sink (TIM between package and heat sink base)
  θ_sa = sink-to-ambient (convection through fins)
```

**Heat sink thermal resistance (θ_sa) estimate:**
```
θ_sa = (T_heatsink_base - T_ambient) / Q_device

PBGA: θ_sa ≈ (85.9 - 20) / 12 ≈ 5.49 °C/W
QFP:  θ_sa ≈ (44.5 - 20) / 8  ≈ 3.06 °C/W
```

### PCB Effective Conductivity

```
k_plane  = Σ(k_i · t_i) / Σ(t_i)   = 23.43 W/m·K  (in-plane)
k_normal = Σ(t_i) / Σ(t_i/k_i)     = 0.3963 W/m·K (through-thickness)
```

---

## Input Parameters Reference Table

### Cabinet & PCB

| Parameter | Value | Unit |
|---|---|---|
| Cabinet X | 0 → 0.4 | m |
| Cabinet Y | 0 → 0.13 | m |
| Cabinet Z | 0 → 0.25 | m |
| Min-X wall | Grille | — |
| PCB dimensions | 0.4 × 0.25 | m |
| PCB Y-position | 0 → 1.6 mm | m |
| PCB material | FR-4 | — |
| PCB substrate thickness | 1.6 | mm |
| Cu layer 1 | 2 Cu-oz/ft², 50% coverage | — |
| Cu layer 2 | 1.5 Cu-oz/ft², 80% coverage | — |
| Cu layer 3 | 2 Cu-oz/ft², 30% coverage | — |
| k_plane (PCB) | 23.43 | W/m·K |
| k_normal (PCB) | 0.396 | W/m·K |

### Packages

| Parameter | PBGA | QFP_1/2/3 |
|---|---|---|
| Package type | 700-BGA, 5-perip | 184-Lead PQFP |
| Package size | 51 mm | 32 mm |
| Die material | Si-Typical | Si-Typical |
| Die size | 15.3 × 15.3 mm | 9.6 × 9.6 mm |
| Die thickness | 0.35 mm | 0.64 mm |
| Total power | 12 W | 8 W each |
| Die pad size | 20.4 × 20.4 mm | 12.8 × 12.8 mm |
| Die pad thickness | 0.1 mm | 0.1 mm |
| Die attach thickness | 0.04 mm | 0.05 mm |

### Heat Sinks

| Parameter | Value |
|---|---|
| Type | Detailed, Extruded |
| Flow direction | X |
| Fin count | 5 |
| Fin thickness | 0.005 m |
| Offset | 0.0 m |
| Material | Aluminium (default) |

### Fans

| Parameter | Value |
|---|---|
| Name | Fan_1, Fan_2, Fan_3 |
| Type | 2D Circular, Intake |
| Plane | Y-Z at x = 0.4 m |
| Radius | 0.025 m |
| Inner radius | 0.02 m |
| Flow type | Fixed |
| Flow rate | 20 CFM each |
| Temperature | Ambient (20 °C) |
| Gauge pressure | 0 N/m² |

### Solver Settings

| Parameter | Value |
|---|---|
| Iterations | 200 |
| Flow convergence | 0.001 |
| Energy convergence | 1×10⁻⁷ |
| Joule heating criterion | 1×10⁻⁷ |
| Mesh type | Mesher-HD, Normal |
| Turbulence model | Zero equation (mixing length) |
| Radiation | Ignored |
| Analysis type | Steady-state |

---

## Observations & Conclusions

### Key Findings

**Thermal Performance:**
- The **PBGA package** is the critical thermal component at **85.9 °C junction temperature** — significantly higher than QFP packages (~44.5 °C) due to its higher 12 W power dissipation and larger die area
- The **QFP packages** remain well within safe limits at ~44.5 °C, with their smaller 8 W die and direct fan alignment providing effective cooling
- **PCB surface temperature** peaks at 35.8 °C near the PBGA — well within FR-4's safe operating limit (~130 °C)

**Aerodynamic Performance:**
- Three 20 CFM fans produce a maximum velocity of **10.33 m/s** in the fin channels
- Pressure drop across the system is approximately **27 N/m²** — driven primarily by the heat sink fin arrays
- Flow uniformity is good across the PCB surface, with each fan aligned to one package row

**Mesh Quality:**
- The 213,689-element mesh shows excellent quality: min face alignment 0.28, dominant skewness near 1.0
- Mesher-HD successfully resolved the thin die attach layers (minimum gap Y = 3.5×10⁻⁵ m)

### Potential Optimisations (for Temperature Reduction)

| Optimisation | Expected Impact |
|---|---|
| Increase PBGA heat sink fin count from 5 to 8 | Reduce θ_sa by ~30%; lower PBGA T_j by ~10–15 °C |
| Add thermal interface material (TIM) between package and heat sink | Reduce θ_cs; lower T_j by ~5 °C |
| Increase fan CFM from 20 to 30 CFM | Higher h; reduce all temperatures by ~5–8 °C |
| Reposition PBGA closer to Fan_2 centreline | Improve flow alignment; reduce T_j by ~3–5 °C |
| Increase heat sink fin height | Greater surface area; lower θ_sa by ~20% |
| Use copper heat sinks instead of aluminium | k_Cu ≈ 2× k_Al; reduce fin-to-tip temperature drop |

### Conclusion

The ANSYS Icepak simulation successfully demonstrates the thermal behaviour of a PCB-mounted multi-package electronic system. The forced-air cooling system with three fans (60 CFM total) maintains all packages at safe operating temperatures at 36 W total power. The PBGA is the thermally critical component and the primary target for any thermal design optimisation. The simulation methodology — from package library selection through detailed mesh quality verification to post-processed contour plots — provides a validated thermal design baseline for further optimisation iterations.

---

## Repository Structure

```
ansys-pcb-thermal-simulation/
│
├── README.md                     ← This file
├── images/                       ← All simulation screenshots (35 images)
│   ├── img_01.jpg                ← Cabinet geometry
│   ├── img_02.jpg                ← Fan placement
│   ├── ...
│   └── img_35.jpg
├── Anirudh_Prasad_Final_Project/ ← ANSYS Icepak project folder
│   ├── Anirudh_Prasad_Final_Project01.aedt
│   └── ...
└── results/                      ← Exported result files (optional)
    ├── solution_overview.txt
    ├── junction_temperatures.csv
    └── pressure_data.csv
```

---

*Simulation performed in ANSYS Icepak 2021 R1 | Steady-state forced convection | Re = 42,143 | Total power = 36 W*
