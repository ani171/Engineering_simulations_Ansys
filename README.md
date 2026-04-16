# Semiconductor Packaging
## Module 1
#### Why is semiconductor packaging needed?
- Semiconductor packaging is the process of enclosing a fabricated silicon die in a protective structure that enables reliable electrical connections between the integrated circuit (IC) and the external system. It acts as the critical interface between the microscopic on-chip circuitry and the macroscopic electronic environment in which the IC operates.
- Although semiconductor dies are fabricated in highly controlled and clean environments, once separated from the wafer, they are exposed to real-world operating conditions. Therefore, packaging plays a vital role in ensuring that the IC can function reliably outside the fabrication facility. The packaging process provides essential mechanical support, electrical interconnection, thermal management, and environmental protection throughout the operational lifetime of the device.
- Specifically, semiconductor packaging:
    1. Enables the die to electrically connect with other dies and external system components.
    2. Protects the semiconductor device from environmental and mechanical hazards such as corrosion, moisture ingress, contamination, and physical damage.

<figure>
  <img width="2497" height="1105" alt="image" src="https://github.com/user-attachments/assets/92db1f73-673d-441e-9cd0-ab48112bc8c1" />
  <figcaption>
    <em>Figure: Semiconductor manufacturing flow from wafer to singulated die and final packaged device</em>
  </figcaption>
</figure>

<br> </br>
#### IC Manufacturing Flow:
<figure>
  <img width="1000" height="800" alt="image" src="https://github.com/user-attachments/assets/0b4aa082-0e2d-4ffb-a42b-fbfbf42a0bc1" />
  <figcaption>
    <em>Figure: Semiconductor industry value chain highlighting IDM, Fabless, Foundry, and OSAT models, showing the flow from design, wafer fabrication, package & test, to final assembly</em>
  </figcaption>
</figure>
<br> </br>
1. Design – Circuit & layout design
   - The design stage involves converting system requirements into a functional integrated circuit. Circuit design defines the electrical behavior of the IC, while layout design translates the circuit into physical geometries on silicon. This stage ensures functionality, performance optimization, and manufacturability through simulations and design rule checks.
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/61aabcca-1cf6-4dbb-987a-5901f435bc06" />

2. Wafer Process – Fabrication of ICs on wafers
  - In this stage, integrated circuits are fabricated on silicon wafers using processes such as lithography, deposition, doping, and etching. Multiple dies are manufactured simultaneously on a single wafer in a controlled cleanroom environment. The objective is to achieve high yield and reliable device characteristics.
3. Package & Test
  - Wafer Test: Individual dies on the wafer are electrically tested to identify good and defective dies before packaging.
  - Packaging: Good dies are separated from the wafer and encapsulated to provide mechanical protection, electrical connectivity, and thermal management.
  - Package Test: Packaged ICs undergo electrical and functional testing to ensure they meet performance and reliability specifications.
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/0dcc9b35-257a-461a-85f8-501763c5b682" /> <br/>
4. Assembly – Final integration into products
  - Packaged semiconductor devices are mounted onto printed circuit boards (PCBs) using surface-mount or through-hole assembly techniques.
  - Electrical and mechanical interconnections are formed through solder reflow or wave soldering processes.
  - Assembled boards are integrated with other subsystems to form complete electronic products.
  - System-level testing and validation are conducted to ensure functional correctness, reliability, and compliance with operational requirements. <br/>

#### Types of Manufacturers: 

| Model | Primary Role | Key Responsibilities | Examples |
|------|-------------|---------------------|----------|
| **IDM (Integrated Device Manufacturer)** | End-to-end semiconductor development | • IC design, fabrication, packaging, and testing handled in-house<br>• Full control over process, yield, and IP<br>• High capital investment required | Intel, Samsung, Texas Instruments |
| **OSAT (Outsourced Semiconductor Assembly & Test)** | Packaging and testing services | • Specializes only in assembly, packaging, and testing<br>• Does not perform IC design or wafer fabrication<br>• Supports both IDMs and fabless companies | ASE, Amkor, JCET |
| **Fabless** | IC design and system architecture | • Focuses only on IC design and verification<br>• Wafer fabrication and packaging are outsourced<br>• Low capital expenditure, high innovation focus | Qualcomm, NVIDIA, AMD |
| **Foundry** | Wafer fabrication | • Manufactures ICs based on customer designs<br>• No involvement in IC design<br>• Operates advanced fabrication nodes | TSMC, GlobalFoundries, UMC |

#### Silicon lifecycle
<img width="541" height="541" alt="image" src="https://github.com/user-attachments/assets/7fcb828b-dfbd-4ff1-b2e8-97e7ae28cfdd" /> <br/>

- **Design**  
  Defines the functionality, architecture, and physical layout of the integrated circuit through circuit design, verification, and layout implementation.

- **Manufacturing**  
  Fabrication of the integrated circuit on silicon wafers using semiconductor processes such as lithography, deposition, and etching in a controlled cleanroom environment.

- **Test**  
  Electrical and functional testing at wafer and package levels to detect defects and verify compliance with design specifications.

- **Debug / Bring-up**  
  Initial validation of first silicon by powering up the chip, identifying functional issues, and optimizing performance.

- **In-Field Operation**  
  Deployment of the IC in real-world applications where it operates throughout its lifetime with reliability monitoring and updates if required.
#### Choosing the right package
1. Application Requirements 
    - The intended application of the IC—whether for memory, logic, analog, or mixed-signal—strongly influences packaging decisions. High-performance applications may require advanced interconnect structures or high bandwidth to support data throughput. The number and type of interconnects directly impact signal integrity and overall system speed.
2. Thermal Dissipation 
    - Heat management is critical in modern ICs. The chip’s power density, along with the choice of substrate and thermal interface materials, determines the package type. High-power or high-temperature chips often require thermally conductive materials like ceramic or metal, as organic laminate substrates may fail under excessive heat.
3. Form Factor 
    - Space constraints in end products dictate package dimensions, including thickness, footprint, and height. Compact form factors are essential for mobile and wearable devices, while larger form factors may be acceptable for desktop or server applications.
4. Reliability 
    - Long-term performance under operating conditions is a key consideration. Packages must maintain electrical and mechanical integrity over the device’s lifetime, including tolerance to temperature cycling, humidity, and power fluctuations.
5. Durability 
    - Packages must withstand mechanical stress during assembly, shipping, and usage. Environmental factors such as vibration, shock, and moisture can influence the choice of protective encapsulation and ruggedization techniques.
6. Cost
    - Cost remains a major driver in package selection. While advanced packaging solutions provide superior performance, they often come at higher manufacturing and material costs. Trade-offs between performance, reliability, and budget are carefully analyzed in industrial settings.

<figure>
  <img width="1263" height="483" alt="image" src="https://github.com/user-attachments/assets/2fed2779-734c-459b-931e-af390548b3a5" />
  <figcaption>
    <em>Figure: Die, carrier, and PCB interconnect hierarchy in a molded semiconductor package</em>
  </figcaption>
</figure>


#### Packaging classification
#### Through-Hole Mounting

Through-hole mounting is a traditional method for attaching electronic components to a PCB, where component leads pass through holes in the board and are soldered on the opposite side. This method provides strong mechanical bonding and is suitable for high-reliability applications.

| Package Type | Full Name | Description | Typical Applications |
|--------------|-----------|-------------|--------------------|
| **TO** | Transistor Outline | Used for discrete components like transistors, diodes, and voltage regulators. Features a metal or plastic body with leads extending through the PCB. Good for heat dissipation when attached to a heat sink. | Power transistors, diodes, voltage regulators |
| **DIP** | Dual Inline Package | Rectangular package with two parallel rows of pins. Easy to handle and solder, suitable for prototyping and through-hole PCBs. | Microcontrollers, memory ICs, logic ICs |
| **PGA** | Pin Grid Array | Array of pins on the underside of the IC that insert into PCB holes. Offers high pin count and reliable connections. Often used for processors. | CPUs, high-pin-count ICs, socketed ICs |

> - Through-hole components are mechanically robust and suitable for high-power or high-stress applications.  
> - PGA packages allow easy replacement of ICs without soldering, ideal for prototyping.

<figure>
  <img width="965" height="387" alt="image" src="https://github.com/user-attachments/assets/8051e685-e3b0-4fad-92c6-cce5ec518c31" />
  <figcaption>
    <em>Figure: Through Hole Technology: Sino Voltaics </em>
  </figcaption>
</figure>

#### Surface Mount Technology (SMT)

SMT allows components to be mounted directly onto the surface of a PCB without passing leads through holes. It enables compact designs, higher pin counts, and faster assembly.

| Package Type | Full Name | Description | Typical Applications |
|--------------|-----------|-------------|--------------------|
| **QFN** | Quad Flat No-Lead | Leadless package with pads underneath. Provides good thermal and electrical performance, very compact footprint. | High-speed ICs, RF modules, power management ICs |
| **QFP** | Quad Flat Package | Leads extend from all sides, making inspection and soldering easier. | Microcontrollers, FPGAs, logic ICs |
| **PBGA** | Plastic Ball Grid Array | Solder balls underneath the package. Offers high I/O density and improved signal integrity. | CPUs, GPUs, memory ICs |
| **LGA** | Land Grid Array | Flat lands instead of solder balls. Used where socketing or fine pitch is required. | High-performance processors, server ICs |
| **CSP** | Chip Scale Package | Package size approximately equals die size. Very compact and similar to BGA. | Smartphones, compact devices, memory ICs |
| **PoP** | Package on Package | Multiple packages stacked vertically. Saves board space, commonly used in mobile devices. | Mobile processors, memory stacking |
| **MCM** | Multi-Chip Module | Multiple dies integrated in a single package. Improves performance and integration density. | High-performance computing, system-in-package applications |
  
> - SMT packages enable miniaturization, automated assembly, and high-density PCB designs.  
> - Selection depends on thermal requirements, pin count, and mechanical constraints.

<figure>
  <img width="980" height="403" alt="image" src="https://github.com/user-attachments/assets/b0a699ee-9d0d-494b-a29b-953f14c0b323" />
  <figcaption>
    <em>Figure: Surface Mount Technology Technology: Sino Voltaics </em>
  </figcaption>
</figure>

#### Advanced Package Substrates

Advanced packaging techniques are used to integrate multiple dies on a single substrate or improve interconnect density, signal integrity, and bandwidth. Key approaches include 2D, 2.1D, 2.3D, and 2.5D packaging.  

#### 2D Package

| Feature | Description | Notes |
|---------|-------------|-------|
| **Die Placement** | Two dies placed on the same substrate (e.g., FCBGA). | Provides a single substrate for multiple dies instead of using two separate substrates. |
| **Die-to-Die Communication** | Communication goes via BGA → substrate → other die. | Relatively longer signal paths than RDL or interposer-based designs. |

#### 2.1D Package 

| Feature | Description | Notes |
|---------|-------------|-------|
| **RDL (Redistribution Layer)** | Adds a layer between die and substrate to reroute connectivity. | Required when die bond pads are small and unevenly distributed compared to substrate pads. |
| **Connectivity** | RDL rearranges die connections to match substrate geometry. | Provides shorter internal connections and improved routing compared to 2D. |
| **Signal Path** | Reduces signal length, improving performance and reducing delay. | Particularly effective for two-die systems. |

> **RDL:**  
> - RDL is typically a thin metal layer (Cu) deposited on a polymer layer.  
> - Requires photolithography to define fine traces.  
> - Enables high-density routing without increasing substrate size.  

<figure>
  <img width="1475" height="933" alt="image" src="https://github.com/user-attachments/assets/0d84b609-254b-4783-bb06-3dfe0ca89b1e" />
  <figcaption>
    <em>Figure: A cross-sectional view of a chip with RDL technology (Source: Hanol Publishing)</em>
  </figcaption>
</figure>

#### 2.3D Package 

| Feature | Description | Notes |
|---------|-------------|-------|
| **Interposer** | Uses an organic interposer between die and substrate to fan out high-density connections. | Supports multiple chips; simpler than RDL for >2 dies. |
| **Power/Ground** | Dedicated planes in interposer for power and ground. | Helps reduce IR drop and improves signal integrity. |
| **Routing** | Organic interposer allows dense fan-out while maintaining manufacturability. | Becomes challenging beyond moderate pin counts compared to silicon interposer. |

> **Organic Interposer:**  
> - Fabricated using laminated organic layers and thin metal traces.  
> - Provides flexibility in routing and is cost-effective compared to silicon interposers.  
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/d6b62ae9-a664-4279-9797-18efeba6b472" />


#### 2.5D Package 

| Feature | Description | Notes |
|---------|-------------|-------|
| **Interposer** | Uses a silicon interposer with passive Through-Silicon Vias (TSVs) to connect die to substrate. | High-density connections with very fine metal layers. |
| **Signal Integrity** | Close proximity of signal lines to ground planes enables controlled impedance and short return paths. | Reduces noise and crosstalk significantly compared to organic interposers. |
| **Performance** | Achieves much higher bandwidth and signal integrity than organic substrates. | Example: CoWoS (Chip on Wafer on Substrate). |

> **Silicon Interposer Manufacturing:**  
> - Interposer made from a silicon wafer with multiple fine metal layers.  
> - TSVs (Through-Silicon Vias) connect top die pads to bottom substrate pads.  
> - Provides high-density fan-out, short interconnects, and improved electrical performance.  

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/9af7816d-c2cb-49d4-8849-8220de0cc0b1" />


<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/949ef62d-97d3-4504-9a24-a3872fadc33f" />

#### Carrier Material Options

| Carrier Type | Description | Typical Applications / Advantages |
|--------------|-------------|---------------------------------|
| **Leadframe** | Metal frame that supports the die and provides electrical connections via leads. Easy to manufacture and cost-effective. | Standard ICs, low-cost logic and memory packages |
| **Laminate** | Layered organic material used as substrate. Lightweight and flexible, suitable for medium-power applications. | BGAs, QFNs, consumer electronics |

> - Carrier selection depends on **thermal, mechanical, and electrical requirements**.  

#### Interconnection Options

| Interconnection Type | Description | Typical Applications / Advantages |
|--------------------|-------------|---------------------------------|
| **Wirebond (Stitch Type)** | Thin metal wire (Au, Cu) connects die pads to package leads. Stitch type is robust and flexible for thermal expansion. | Standard ICs, TO packages, low- to medium-pin-count packages |
| **Bump / Solder** | Solder or micro-bumps form connections between die and substrate, used in flip-chip assemblies. | High-density BGAs, CSPs, advanced 3D packages |

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/6e1b71fe-7428-4ba8-b433-f2156fd5dad2" /> <br/>


## Module 2

### Supply chain
| Stage | Description | Key Activities | Industry Focus |
|------|-------------|----------------|----------------|
| **1. Design House** | IC design is performed using EDA tools, resulting in a finalized GDS II file for fabrication. | - RTL, logic, and physical design <br> - Verification (functional, timing, power) <br> - Use of foundry PDKs and design rules | Performance, power, area (PPA), design correctness |
| **2. Wafer Fabrication** | ICs are fabricated on silicon wafers in a semiconductor foundry. | - Silicon wafer processing <br> - Lithography, etching, deposition <br> - Use of gases, chemicals, materials, and advanced equipment | Yield, process control, defect reduction |
| **3. Package Assembly & Test** | Individual dies are assembled into packages and electrically tested. | - Wafer probing, dicing <br> - Die attach, wirebond or flip-chip <br> - Package test and burn-in | Reliability, thermal performance, cost |
| **4. Board Assembly & Test** | Multiple packaged ICs are assembled onto a PCB and validated as a system. | - SMT/through-hole assembly <br> - Reflow soldering <br> - Board-level functional and electrical testing | Signal integrity, manufacturability |
| **5. Product Assembly & Test** | Final product is assembled and validated before shipment. | - Mechanical integration <br> - Firmware/software loading <br> - System-level and environmental testing | Product quality, compliance, customer reliability |

### Packaging process

##### 1. Wafer Preparation (ISO Class 7)
- Wafers are received in carriers and prepared for processing in a controlled cleanroom environment.
- ISO Class 7 ensures low particulate contamination to prevent defects during subsequent steps.

##### 2. Wafer Inspection
- Visual and automated inspection is performed to detect defects or contamination before processing.
- Ensures only high-quality wafers proceed to the next stages.

| Test Type | Purpose | Process | Advantages | Applications |
|-----------|---------|--------|------------|-------------|
| **Wafer Automated Test (WAT)** | Detect visual defects or process-related issues on the wafer surface before electrical testing. | - Automated optical inspection (AOI) scans the wafer for defects like scratches, contamination, pattern misalignment, or missing features. <br> - Machine vision compares the wafer to a reference pattern to locate anomalies. | - Non-contact and high-speed inspection. <br> - Identifies defective areas early, saving cost by preventing the processing of bad dies. | - Early detection of lithography or etching defects. <br> - Monitoring yield trends in manufacturing. |
| **Wafer Probe Test (Electrical Test)** | Verify the electrical functionality of each die before dicing. | - A **probe card** with tiny needle contacts each die pad. <br> - Electrical signals are applied, and die responses are measured. <br> - Dies are classified as **good (pass)** or **bad (fail)**. | - Early identification of faulty dies prevents packaging of defective ICs. <br> - Provides data for yield analysis and process optimization. | - Logic ICs, memory ICs, and analog/mixed-signal devices. <br> - Performed at the wafer level before assembly and packaging. |

##### 3. Front-Side Tape Lamination
- Protective tape is applied on the wafer front-side to protect circuitry during thinning and handling.
- Prevents mechanical damage and contamination during back grinding and dicing.

##### 4. Wafer Back Grinding
- The wafer is thinned to the required thickness.
- The circuit/pattern is only on the top side; the bottom silicon is primarily for mechanical support.
- Thinning reduces package height and prepares wafers for assembly while maintaining die integrity.

<img width="1395" height="489" alt="image" src="https://github.com/user-attachments/assets/464dbb35-47f5-41dd-9910-181ad9f974eb" />

##### 5. Tape Frame Mounting to Wafer Backside
- The thinned wafer is mounted onto a tape frame for mechanical support.
- Ensures stability and prevents damage during dicing.

##### 6. Wafer Dicing
- Wafers are separated into individual dies using laser grooving, blade dicing, or a combination of both.
- Precision dicing ensures minimal chipping and maintains die quality for packaging.

| Dicing Type | Description | Advantages | Typical Applications |
|-------------|-------------|------------|--------------------|
| **Blade Dicing** | Mechanical dicing using a diamond-tipped blade to cut the wafer along predefined streets. | - Simple and cost-effective <br> - High throughput for standard wafers | Standard logic ICs, memory ICs, low-thickness wafers |
| **Laser Dicing** | Uses a focused laser beam to cut or scribe the wafer. It can be a UV or an IR laser, depending on the material. | - Contactless, reducing mechanical stress <br> - Can dice very thin or fragile wafers | High-precision ICs, MEMS, advanced packaging |
| **Stealth Dicing** | Laser creates a modified layer inside the wafer that allows it to be separated mechanically along the laser path. | - Minimal chipping <br> - High wafer strength retained <br> - Suitable for thin wafers | High-performance chips, advanced memory, sensitive wafers |
| **Plasma Dicing** | Wafer is etched along streets using plasma to separate dies without mechanical contact. | - No mechanical stress <br> - High precision and minimal chipping <br> - Suitable for ultra-thin wafers | MEMS, sensors, high-reliability devices |

##### **Wire bond packaging**
  - Using a wafer map, known good dies are picked and placed onto the substrate (leadframe or laminate)
  - *Die attach* is performed using epoxy; the epoxy deposition pattern directly affects die attach quality and reliability
  - After die attach, curing is performed
  - Wire Bonding <br/>
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ccb5cf2b-4dd4-4cf6-b209-d0da41aa8ba3" /> <br/>
  - Molding compound transfer - Encapsulation of die and wires using molding compound - Resin flow method
  - Marking - Package labeling with part number, lot, and traceability information to identify the package
  - Package dicing <br/>
##### **Flip chip packaging**

| Step | Process | Description |
|-----|--------|-------------|
| 1 | **Flipping the Chip** | Die is flipped so solder bumps face downward toward the substrate. |
| 2 | **Die Placement** | Die is placed on the substrate, which already has matching bond pads. Flux is applied to assist solder wetting. |
| 3 | **Thermocompression Attach** | Heat and pressure are applied to attach the solder bumps to substrate pads. |
| 4 | **Solder Reflow** | Solder melts and forms reliable electrical and mechanical joints between die and substrate. |
| 5 | **Flux Cleansing** | Residual flux is removed using solvent spray to prevent corrosion and reliability issues. |
| 6 | **Underfill Dispensing** | Epoxy underfill is injected between die and substrate to reduce thermo-mechanical stress and improve joint reliability. |
| 7 | **Underfill Cure** | Underfill material is cured to achieve mechanical strength and long-term reliability. |
| 8 | **Molding** | Encapsulation material is applied to protect the die and interconnections. |
| 9 | **Marking** | Package is marked with identification, lot number, and traceability information. |
| 10 | **Ball Mounting & Reflow** | Solder balls are mounted on the substrate side and reflowed to enable PCB-level connections (BGA). |

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ed773c0f-e712-4619-9dc1-c28a2f104f15" />

<img width="500" height="250" alt="image" src="https://github.com/user-attachments/assets/d29fa7e3-a1b4-4836-a00e-6d4850816707" />

#### Wafer-level Packaging
- Wafer-level packaging performs most packaging steps at the wafer stage, enabling ultra-thin packages, shorter interconnects, and improved electrical performance.

##### WLCSP (Wafer-Level Chip Scale Package)
- Package size is approximately equal to the die size.
- Redistribution Layer (RDL) and solder bumps are formed directly on the original wafer.
- Limited I/O count due to die-size constraint.
- Widely used in compact and low-power mobile devices.

##### FI-CSP (Fan-In Chip Scale Package)
- I/O pads are routed within the die footprint
- Simple structure with lower cost compared to fan-out solutions.
- Limited scalability for high I/O counts.
- Suitable for small dies with modest connectivity needs.
- Common in sensors and low-pin-count ICs.
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/793d79f1-1070-424c-abf4-b1d7618bb4ed" />

##### Reconstitution Process
- Known Good Dies (KGDs) are picked from the original wafer and placed on a temporary carrier.
- Dies are arranged in a predefined layout to enable fan-out routing.
- Molding compound is applied to encapsulate the dies.
- The temporary carrier is removed, forming a reconstituted wafer
- This wafer is used for RDL formation, bumping, and further processing.

##### FO-WLP (Fan-Out Wafer-Level Packaging)
- Uses a reconstituted wafer where known good dies are embedded in molding compound.
- Redistribution Layers (RDL) are formed to fan out I/O pads beyond the die footprint.
- Supports higher I/O density compared to WLCSP and FI-CSP.
- Enables thinner packages with improved electrical and thermal performance.
- Eliminates the need for a laminate substrate.
- Commonly used in application processors, RF ICs, and high-density mobile devices.
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/321a5eae-661a-4576-b9f6-b8c781da4a84" />

##### InFO-oS (Integrated Fan-Out on Substrate)
- Combines fan-out RDL technology with a substrate.
- Improves power delivery, mechanical strength, and routing capability.
- Supports higher bandwidth and better signal integrity.
- Reduces package thickness compared to traditional flip-chip packages.
- Widely used in high-performance mobile SoCs.
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/4e48e7ca-e957-4ae5-b0e2-1f0551cee869" />

##### InFO-PoP (Integrated Fan-Out Package-on-Package)
- Fan-out package designed to support vertical stacking of memory on logic die.
- Enables tight integration of processor and DRAM.
- Reduces signal latency between logic and memory.
- Saves board space in mobile applications.
- Commonly used in smartphones and compact consumer electronics.
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/d8e42af0-0d8d-49c1-b18a-3c6a035606d1" />


## Module 3 
### Ansys Icepak Lab – Thermal Analysis of a Flipchip BGA 
- Electronic devices consume power and generate heat as they operate. This heat raises the temperature of components that include semiconductor products, which can compromise the functionality, reliability, and safety of electronic equipment. Therefore, electronic equipment must have proper cooling systems to keep the temperature of components below a certain level in any environment.
- Thermal analysis, thus, becomes an essential test as heat dissipation is one of the crucial roles of semiconductor packages. Therefore, generated heat, the heat dissipation effect of the package material and structure, and the temperature effect when the semiconductor package is applied to the system must be accurately understood in advance to be reflected in the package design.
- In order to perform and utilize thermal analysis on a semiconductor package, it is necessary to define the key temperature points on the package. The main temperature points of the package are ambient temperature (Ta), junction temperature (Tj), case temperature (Tc), and board temperature (Tb). The temperature for package specifications is usually either Tj max. or Tc max., terms which refer to the maximum temperature that ensures the semiconductor device operates normally. 

<figure>
  <img width="1344" height="549" alt="image" src="https://github.com/user-attachments/assets/b9b3091c-90cc-4c98-ba75-b1b4fc945c91" />
  <figcaption>
    <em>Figure: Key temperature points of the package (Source: SK Hynix Newsroom)</em>
  </figcaption>
</figure>

| Symbol | Name                              | Formula     |
|--------|-----------------------------------|------------|
| Ja     | Junction-to-ambient thermal resistance | (Tj-Ta) / P |
| Jc     | Junction-to-case thermal resistance    | (Tj-Tc) / P |
| Jb     | Junction-to-board thermal resistance   | (Tj-Tb) / P |


#### Step 1: 
- Insert Icepak Design
- Open ANSYS Workbench
- Navigate to: `Project → Insert → Icepak Design`
#### Step 2: 
- Open the Icepak Layout
- Click the Icepak tab in the top toolbar
- This launches the Icepak layout environment

|   |
|---|
|<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/38ff30d0-6e11-448d-a16b-dbd35bf0218e" />|

#### Step 3: 
- Create a Flip-Chip BGA Package
- Navigate to: `Icepak → Toolkit → Geometry → Packages → Flipchip_BGA`
- A configuration window will appear
- Set the following parameters:
    - xLength: 15 mm
    - yLength: 15 mm
    - Package Thickness: 3 mm
    - Model Type: Detailed
    - Symmetry: Full
- Click OK to generate the 3D model
- The Flip-Chip BGA package will appear in the working space

|   |   |   |
|---|---|---|
| <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/b04ea4e2-0967-4292-a2c0-4c61547a2f7c" /> | <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/91161ca0-e78c-4f65-80a4-ab4bd31fcdb4" /> | <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/de148fc2-e206-4016-b658-66b7dc75312e" /> |


#### Step 4:
- In the Model Tree, expand the Solids section
- Observe the generated components, such as:
    - Substrate
    - Die
    - Underfill
    - Other package elements

|   |   |
|---|---|
| <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/0a9afe1a-82f8-4fe5-8b60-dd030045397a" />| <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/1ab05be0-2f96-45c0-bdb6-c9bd5e3c438c" /> | <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/eff79f80-fa28-4dd8-bca7-903ee1331433" /> |

#### Step 5: 
- Assign Thermal Power
- Navigate to: `Project Manager → Thermal`
- Enter the Power value (e.g., 1 W)
- Click OK

|   |
|---|
| <img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/17658342-00e6-4bb5-8ac1-0282af42543f" /> |

#### Step 6: 
- In Solids, select Flipchip-BGA1_substrate
- `Right-click → Assign Thermal → Source`
- In the dialog box:
    - Set Thermal Condition to Fixed Temperature
- Click OK
- Delete any unnecessary thermal elements (e.g., Flipchip_BGA_trace1) under the Thermal node
<br> </br>

|   |
|---|
| <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/dc91fbbb-de88-4e82-8e26-6914bbd1dcdb" /> |

#### Step 7: 
- Assign Temperature Monitors
- In Solids, select Substrate
- `Right-click → Assign Monitor → Point`
- Enable Temperature → Click OK
- Repeat the same steps for:
    - Die
    - Underfill
<br> </br>

|   |   |   |
|---|---|---|
| <img width="800" height="1000" alt="image" src="https://github.com/user-attachments/assets/3b4439e2-3c9b-459d-842b-76500e81bfbc" />| <img width="800" height="1000" alt="image" src="https://github.com/user-attachments/assets/c7368faf-ead4-4e6e-9b8e-309d3e36931f" /> | <img width="800" height="1000" alt="image" src="https://github.com/user-attachments/assets/41afeaef-24a9-4077-8ca2-b34347690060" /> |

#### Step 8: 
- Generate Mesh
- Navigate to the Mesh tab
- Click: `Simulation → Generate Mesh`
- Save the file when prompted
- Click OK
<br> </br>

|   |
|---|
| <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/ecf2fd8f-132a-4814-8b61-17591282a380" /> |

#### Step 9: 
- Inspecting Mesh Quality
- Open Mesh Visualization
- Click Quality
- Verify mesh parameters such as:
    - Face Alignment
    - Skewness
<br> </br>

|   |   |
|---|---|
| <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/e881404d-4cd9-4bf8-a890-81b56d7a1b3e" /> | <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/d3672a0e-3839-4fdf-9e6d-0b3a525c94dd" /> |


#### Step 10: 
- Click Validate from the top menu bar
- Ensure all checks return green ticks
- This confirms the model is ready for simulation
<br> </br>

|   |
|---|
| <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/84e7e7aa-6f37-4141-854b-9c38afea6ed2" /> |

#### Step 11: 
- Click Analyze All from the top toolbar
- Select the Flip-Chip BGA package
- Navigate to: `Plot Field → Temperature → Temperature`
- Configure Output Options:
    - Enable Specify Name
    - Enable Specify Folder
    - Enable Plot on Surface Only
    - Under Surface Smoothing, enable Gaussian Smoothing
- Click OK, then Done

|   |
|---|
| <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/dd32072e-ed58-4a50-aac6-3cf5487b69ce" /> |

## Module 4

- Testing at different stages
    1. Wafer Probe Test 
        - Electrical testing is performed directly on dies while they are still on the wafer.
        - Probe cards make temporary contact with die pads to verify basic functionality.
        - Key parameters such as continuity, leakage, timing margins, and voltage limits are checked.
        - Identifies Known Good Dies (KGDs) before dicing and packaging.
        - Prevents expensive packaging of faulty dies.
    2. Wafer Sorting 
        - Test results from wafer probe are used to classify dies into **bins** (good, marginal, bad).
        - A wafer map is generated indicating the exact location of good and bad dies.
        - Sorting information is used by die pick-and-place machines during assembly.
        - Enables yield tracking and process tuning at the foundry.
        - Bad dies are automatically skipped during packaging.
    3. Package Testing 
        - Electrical and functional tests are performed after the die is assembled into a package.
        - Verifies solder joints, wire bonds, flip-chip connections, and package integrity.
        - Tests include parametric tests, functional vectors, and sometimes burn-in.
        - Detects failures introduced during assembly or packaging.
        - Ensures only fully functional ICs move to board-level assembly.
    4. System-Level Testing
        - ICs are tested in **real operating conditions** on evaluation boards or end systems.
        - Validates performance under actual voltage, temperature, and workload scenarios.
        - Catches issues not visible in standalone IC tests (timing interactions, thermal stress).
        - Often used for automotive, networking, and high-reliability products.
        - Acts as the final quality gate before mass production or customer shipment.

### Package testing 
1. Assembly open and short test
2. Burn-in - Apply thermal and voltage stress to ensure early life reliability
3. Final test - Cold and hot test for validating functional and parametric specs across various temperatures

| Test Stage | Purpose | What is Done in Industry | Key Outcomes |
|-----------|---------|--------------------------|--------------|
| **AOST (Assembly Open Short Test)** | Quickly screen for major assembly defects. | - Electrical check for opens and shorts on package leads or solder balls <br> - Vision inspection to detect missing, damaged, or misaligned balls/leads | - Early rejection of gross failures <br> - Prevents bad parts from leaving assembly |
| **Burn-in Test** | Identify early-life (infant mortality) failures under stress. | - Devices are loaded from trays onto burn-in boards <br> - Boards are placed inside burn-in ovens <br> - High temperature and high voltage are applied for extended duration | - Detects dielectric breakdown, metallization defects, electromigration <br> - Improves long-term reliability <br> - May slightly reduce total component lifespan |
| **Final Test** | Ensure packaged IC meets datasheet specifications at temperature corners. | - Devices tested at hot/cold/room temperatures <br> - Loaded into temperature-controlled fixtures <br> - Automatic Test Equipment (ATE) applies test patterns (ATPG) | - Final pass/fail decision <br> - Yield, test time, and coverage are key KPIs |

#### Final Test categories
| Test Type | Description | Industry Objective |
|----------|-------------|-------------------|
| **Parametric Tests** | Measure voltage, current, leakage, and threshold parameters. | Ensure circuits operate within specified electrical limits. |
| **Functional Tests** | Verify correct logical and operational behavior under normal conditions. | Confirm full functionality of the IC. |
| **Speed Tests** | Measure maximum operating frequency and timing margins. | Speed binning and product segmentation based on performance grades. |

#### Bathtub Curve – Failure Rate vs Time
The Bathtub Curve is a reliability model widely used in the semiconductor industry to describe how the **failure rate of an electronic device changes over its lifetime**. It helps manufacturers understand device behavior, plan testing strategies, and ensure long-term product reliability.

<img width="1000" height="545" alt="image" src="https://github.com/user-attachments/assets/d8b0bcfc-d50f-4cf9-8dc8-7ed25ae88ae2" />

1. Early Life Region (Infant Mortality)
- This phase shows a **high initial failure rate** that decreases rapidly with time.
- Failures occur due to:
  - Latent manufacturing defects
  - Process variations
  - Weak interconnects or marginal devices
- Devices that survive this phase are generally robust and stable.
- Eliminating early failures prevents defective products from reaching customers.
- Improves outgoing quality and reduces warranty returns.

2. Useful Life Region (Normal Operating Period)
- Failure rate remains **low and nearly constant**.
- Devices operate within specified electrical and environmental limits.
- Failures are random and not related to manufacturing defects.
- This region represents the guaranteed operating lifetime of the product.
- Reliability predictions, field failure rates, and quality metrics are based on this phase.
- Ensures customer confidence and consistent system performance.
3. Wear-Out Region (End of Life)
- Failure rate increases with time due to aging mechanisms.
- Common causes include:
  - Electromigration
  - Dielectric breakdown
  - Thermal and mechanical fatigue
- Devices eventually degrade beyond acceptable limits.
- Helps define product lifetime and reliability limits.
- Guides material selection, design margins, and qualification standards.
- Prevents unexpected failures in long-term applications such as automotive and aerospace systems.

### Automatic Test Equipment (ATE)

- Used to automatically test integrated circuits for electrical correctness, performance, and reliability at different manufacturing stages.
- Applies input signals to the device under test (DUT) and measures output responses to verify expected behavior.
- Enables high-speed, high-volume testing, making it suitable for mass semiconductor production.
- Ensures each IC meets datasheet specifications before shipment to customers.
- Helps identify manufacturing defects early, reducing field failures and warranty costs.
- Provides consistent and repeatable test results, minimizing human error.
- Test data from ATE is used for yield analysis, process monitoring, and continuous improvement.
- Plays a critical role in maintaining product quality and reliability in automotive, consumer, and industrial electronics.
<figure>
  <img width="998" height="529" alt="image" src="https://github.com/user-attachments/assets/bc80dcdd-950f-42a7-9b3b-db930ba4ae3e">
  <figcaption><em>Figure:Testamatic Systems: Automated Test Equipment and Industrial Automation</em></figcaption>
</figure>/>


## Module 5
### Model the Wire Bond Package in Ansys AEDT 
The main focus of this lab exercise is to build the complete cross-section of a wire bond package, including die, substrate, bonding wires, and mold compound, rather than performing any simulation or analyses.
<figure>
  <img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/124409f2-b7b2-487b-a54a-425fe4772a00" />
  <figcaption><em>Figure:Step-by-step process of modeling a wire bond package in Ansys AEDT, from wafer preparation to electrical testing <./em></figcaption>
</figure>/>

#### Wire Bond Package Specifications

| Component          | Dimensions (mm)   | Position (X,Y,Z) (mm) | Thickness (mm) | Material / Type           | To be noted         |
|-------------------|-----------------|----------------------|----------------|--------------------------|----------------------------------|
| **Die**           | 3 x 3           | (0, 0, 0)            | 0.2            | Silicon                  | Centered at origin               |
| **Substrate**     | 5 x 5           | (-1, -1, -0.5)       | 0.5            | FR4                      | Positioned below die (-Z)       |
| **Epoxy**         | 3 x 3           | (0, 0, 0)            | -0.1           | Modified Epoxy           | Between die and substrate       |
| **Die Bond Pad 1**| 0.2 x 0.2       | (0.2, 0.2, 0.2)      | 0.005          | Metal Pad(Cu)            | On die                          |
| **Die Bond Pad 2**| 0.2 x 0.2       | (0.5, 0.2, 0.2)      | 0.005          | Metal Pad(Cu)            | On die                          |
| **Substrate Pad** | 0.2 x 0.2       | (0.2, -0.8, -0.1)    | 0.005          | Metal Pad(Cu)            | On substrate                    |
| **Bond Wire**     | -               | -                    | 0.025 (diam.)  | Gold                     | h1 = 0.2mm, h2 = 0.305mm       |
| **Molding Compound** | 5 x 5        | (-1, -1, -0.1)       | 1.2            | Epoxy_Kevlar             | Encapsulating package           |


#### Step 1: 
- Launch ANSYS Electronics Desktop
- Select Q3D Layout Design to create a new project

|   |
|---|
| <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/c9498c4d-1f8e-457a-9745-8845fe8cf57b" /> |

#### Step 2: Create the Die
- Navigate to: `Modeler → Surface → Rectangle`
- Draw a rectangular surface to represent the die
- Set the die thickness to 0.2 mm
- Rename the object to die
- Assign material: Silicon

| Die Geometry| Die Material selection |
|----------------------------|----------------------------|
| <img width="400" height="839" alt="image" src="https://github.com/user-attachments/assets/9ebc1f17-0247-440a-8571-91b4afe423c0" />| <img width="400" height="839" alt="image" src="https://github.com/user-attachments/assets/040f3c03-d5ac-4b44-a60a-1120decca009" />|

#### Step 3: Create the Substrate
- Draw another rectangle using the same tool
- Set the substrate size to 5 mm × 5 mm
- Thicken the rectangle to –0.5 mm to form the substrate body
- Rename the object to substrate
- Position the die on top of the substrate by setting its coordinates to: (x = –1, y = –1, z = –0.1)

|   |
|---|
|<img width="500" height="649" alt="image" src="https://github.com/user-attachments/assets/00f652e9-0f4c-43c2-98e1-cacbdf2a5a37" />|


#### Step 4: Add Die Attach Layer
- Create a rectangle matching the die dimensions at the origin (0, 0, 0)
- Set the thickness to –0.1 mm
- Assign the material modified_epoxy to enable thermal conductivity analysis

#### Step 5: Add Die Pad and Substrate Pad
- Create a thin rectangular surface to represent the die pad
- Set the thickness to 0.005 mm


|   |   |   |   |
|---|---|---|---|
| <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/a2411daa-59cf-4f07-b4e0-259e099480ca" />| <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/35aaa2a4-82b4-4e66-a4fb-5aa233c925cd" /> |<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/2b8c7c41-a299-4026-b2fe-4d376c5f9a67" /> | <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/bda5df8d-2ddb-4fbe-b73a-e7719d241373" /> |


#### Step 7: Connect Pads Using Bond Wires
- Use the Bondwire tool
- Connect the die bond pads to the substrate pads
- Assign gold as the bond wire material

|   | 
|---|
| <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/9a6ae63c-69c5-4d80-bd8d-c475003dcd71" /> |

#### Step 8: Add Mold Compound
- Create a rectangular mold compound to encapsulate the die and bond wires
- Set the mold thickness to 1.2 mm
- Assign an epoxy molding compound (EMC) material

|   | 
|---|
| <img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/2ebf7eb3-493a-4b94-ae72-cacbe873dab1" /> |
