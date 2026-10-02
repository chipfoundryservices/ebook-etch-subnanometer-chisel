# Chapter 5: Atomic Layer Etch (ALE)
## Self-Limiting Reactions and Angstrom-Scale Precision

---

## 5.1 The Atomic Layer Dream

In 2016, a fundamental limitation of plasma etching became undeniable:

**No matter how hard you optimize, continuous plasma etch cannot achieve better than ±2–3 nm etch uniformity over a large wafer.**

The problem is statistical. Plasma density, ion energy, and radical concentration vary across the wafer (±5–10%). These variations accumulate into etch rate variations. You cannot engineer it away.

But as transistors shrink below 10nm, the tolerance is tighter. For a Gate-All-Around (GAA) transistor at 3nm node, the gate dielectric thickness is 1.5nm. Etch uniformity of ±2nm is unacceptable—you etch through the dielectric entirely.

**The dream:** Control etch *per atom*, not per nanometer.

**The solution:** Atomic Layer Etch (ALE).

---

## 5.2 The ALE Concept: Self-Limiting Reactions

### 5.2.1 The Reaction Mechanism

ALE uses a **pulsed, cyclic process** with two alternating half-reactions:

**Step 1: Selective Adsorption**
A reactive species selectively adsorbs (sticks) to the surface in a self-limiting monolayer:

$$\text{Surface} + \text{Reactant} \rightarrow \text{Surface-Reactant (1 ML)}$$

The key: The reaction stops after a single monolayer. Why? Because:
- Bare silicon has reactive dangling bonds
- Once covered by one layer of reactant, the surface becomes inert
- Further reactant cannot adsorb

**Step 2: Selective Desorption**
An ion beam selectively removes the adsorbed monolayer:

$$\text{Surface-Reactant} + \text{Ion} \rightarrow \text{Surface} + \text{Volatile product}$$

The key: Low-energy ions (20–50 eV) selectively desorb the surface layer without damaging the substrate.

**Step 3: Purge**
Gas is purged from the chamber to remove reaction byproducts.

**Step 4: Repeat**
The cycle repeats. Each cycle removes exactly one atomic layer (~0.15–0.3 nm).

---

### 5.2.2 The ALE Reaction Sequence: A Concrete Example

**Scenario: Removing silicon with an ALE process**

**Step 1 (Adsorption):** Cl₂ gas is introduced. Chlorine chemisorbs to exposed silicon:

$$\text{Si} + \text{Cl}_2 \rightarrow \text{Si—Cl}_2 + \text{H}_2$$

(The hydrogen comes from residual water; details vary by implementation.)

Why self-limiting?
- Bare Si has reactive bonds
- Si—Cl₂ coating is unreactive to further Cl₂
- No more adsorption occurs

**Step 2 (Desorption):** Low-energy Ar⁺ ions (30 eV) strike the wafer:

$$\text{Si—Cl}_2 + \text{Ar}^+ \rightarrow \text{Si} + \text{SiCl (volatile)} + \text{Ar}$$

The Ar⁺ ion is energetic enough to break the Si—Cl bond and eject the chlorine, but *not* energetic enough to knock out a Si atom from the underlying substrate.

**Step 3 (Purge):** Ar gas flow removes volatile byproducts.

**Result:** Exactly one monolayer (0.23 nm) of silicon is removed per cycle.

---

## 5.3 Achieving True Angstrom-Scale Precision

### 5.3.1 Process Control

To achieve this level of precision, the fab must:

1. **Precisely meter the reactant dose:** Ensure exactly one monolayer adsorbs (not 0.5 or 1.5)
2. **Control ion energy tightly:** 30 eV ± 5 eV to avoid over-etching or under-etching
3. **Measure etch depth continuously:** Optical or acoustic methods to confirm layer removal
4. **Repeat precisely:** Each cycle must be identical

**Typical process parameters:**

| Parameter | Value |
|-----------|-------|
| Temperature | 50–100 °C |
| Adsorption step duration | 2–5 seconds |
| Adsorption reactant pressure | 1–10 Torr |
| Ion desorption step duration | 5–10 seconds |
| Ion energy | 20–50 eV |
| Ion flux | 10¹⁶ cm⁻² s⁻¹ |
| Purge step duration | 2–5 seconds |
| Cycle time | 15–30 seconds |
| Etch rate | 0.1–0.3 nm/cycle |

---

### 5.3.2 Process Variation Within a Cycle

Even within a single ALE cycle, variations exist:

**Adsorption phase:**
- If temperature is too high, desorption occurs during adsorption (fewer atoms stick)
- If pressure is too low, incomplete monolayer forms
- If exposure time is too short, incomplete monolayer

**Ion desorption phase:**
- If ion energy is too high, substrate atoms are sputtered (etch is no longer selective)
- If ion flux is too low, some adsorbed atoms remain (incomplete removal)

A fab must control these within tight tolerances:
- Temperature: ±10 °C
- Pressure: ±20%
- Ion energy: ±10%
- Ion flux: ±10%

Process windows are measured in single-digit percentages.

---

## 5.4 ALE vs. Conventional RIE: A Comparison

| Aspect | Conventional RIE | ALE |
|--------|------------------|-----|
| **Control mechanism** | Radical chemistry + ion bombardment | Self-limiting reactions |
| **Etch per cycle** | 50–200 nm continuous | 0.1–0.3 nm per cycle |
| **Uniformity (within-wafer)** | ±2–3% (2–5 nm variation) | ±5% (0.01–0.02 nm variation) |
| **Charge damage risk** | High (ions 50–300 eV) | Low (ions 20–50 eV) |
| **Selectivity** | Moderate (10–20:1) | Excellent (1000:1 possible) |
| **Process time** | 2–5 minutes | 30–60 minutes |
| **Production throughput** | High (100+ wafers/day) | Lower (20–50 wafers/day) |
| **Capital equipment cost** | $10–15M | $12–18M |

---

## 5.5 Applications of ALE

### 5.5.1 Gate Dielectric Thickness Control

In 3nm and below nodes, the gate dielectric (SiO₂ or high-κ oxide) is only 1.5–2.0 nm thick.

Using conventional RIE with ±2 nm uniformity:
- Some regions: 0.0 nm (over-etched, exposed Si)
- Other regions: 4 nm (under-etched, oxide remains)

Device fails electrically in both cases.

With ALE:
- Dielectric thickness: 1.8 ± 0.05 nm across entire wafer
- All devices function within spec

**Impact:** ALE enables GAA (Gate-All-Around) transistors, a key architecture for sub-3nm nodes.

---

### 5.5.2 Selective Si/SiGe Etch (for Nanosheet Release)

In Gate-All-Around transistors, a silicon nanosheet sits surrounded by Si₀.₇Ge₀.₃ (silicon-germanium) sacrificial layers.

To release the nanosheet, the SiGe must be selectively etched away.

**Conventional RIE challenge:**
- Si—Ge bonds are nearly as strong as Si—Si bonds
- Selectivity between Si and SiGe is inherently poor (~2–3:1)

**ALE solution:**
Using a Cl-based ALE chemistry:
- SiGe adsorbs chlorine readily (Ge is more reactive)
- Silicon adsorbs chlorine slowly
- By controlling adsorption time precisely, SiGe is attacked while Si is spared

Selectivity can reach 1000:1 or better.

---

### 5.5.3 Hard Mask Etch

A hard mask is a layer (e.g., Si₃N₄) used as a template for etch.

At sub-5nm nodes, hard mask thickness must be precisely controlled—too thick and it blocks etch, too thin and it erodes.

ALE enables precise thickness control, ensuring consistent masking performance across the wafer.

---

## 5.6 Commercial ALE Implementations

### 5.6.1 Lam Research ALE Systems

Lam's **Sense** platform (introduced ~2018) implements ALE for selective etch applications.

Key features:
- Decoupled adsorption and desorption phases
- Plasma source (ICP) for radical generation during adsorption
- Low-energy ion source for selective desorption
- Real-time etch depth monitoring via optical and RF impedance sensors

---

### 5.6.2 Applied Materials ALE

Applied Materials has introduced ALE capabilities in their advanced etch platforms.

Both companies hold multiple patents covering ALE chemistry, process control, and equipment design.

---

## 5.7 The Limitations of ALE

### 5.7.1 Throughput Penalty

ALE is slow. A conventional etch that takes 2 minutes (RIE, 100 nm deep) might require 15–20 minutes via ALE (0.1 nm per cycle × 1000 cycles = 15 cycles × ~1 minute per cycle).

Fab throughput drops significantly. To maintain capacity, more chambers are needed.

---

### 5.7.2 Thermal Budget

ALE requires lower temperatures (50–100 °C) than conventional etch (often ~100–200 °C). This is to prevent thermal desorption during the adsorption phase.

Lower temperatures can cause other problems:
- Resist degradation
- Resist pattern distortion (PMMA and other polymers are temperature-sensitive)

The process window shrinks further.

---

### 5.7.3 Chamber Complexity

ALE chambers are significantly more complex than conventional RIE:
- Multiple gas sources (etchant, inert carrier, purge gas)
- Precise temperature control
- Low-energy ion generation (more sophisticated than high-energy RIE)
- Real-time monitoring and feedback control

Capital cost: $15–18M per chamber.

---

## 5.8 The Future: Hybrid RIE-ALE Processes

Modern fabs are adopting **hybrid approaches**:

**Step 1: Conventional RIE**
Etch 80% of the depth using high-rate RIE (5 minutes, high throughput)

**Step 2: ALE Selectivity Step**
Etch the final 20% using ALE (10 minutes, high precision and selectivity)

**Result:**
- Overall process time: 15 minutes (compared to 20+ minutes for pure ALE)
- Precision: ±0.1 nm at the critical interface
- Throughput: manageable

This hybrid approach is becoming standard in advanced logic fabs.

---

## 5.9 Key Takeaways: Atomic Layer Etch

1. **ALE is fundamentally different from continuous etch.** Self-limiting reactions replace continuous plasma chemistry.

2. **Precision is the key advantage.** ±5% uniformity (0.02 nm variation) vs. ±2–3% for RIE (2–5 nm variation).

3. **Low ion energy prevents charge damage.** 20–50 eV ions are gentle enough for sensitive dielectrics.

4. **Selectivity can exceed 1000:1.** Selective Si/SiGe removal becomes possible.

5. **Throughput is the main penalty.** ALE is 5–10× slower than conventional etch.

6. **Process windows are very narrow.** Precise control of temperature, pressure, ion energy, and timing is essential.

7. **Hybrid RIE-ALE is becoming standard.** High-rate RIE for bulk removal, ALE for precision finishing.

8. **ALE enables sub-3nm node devices.** Gate dielectric precision, nanosheet release, and hard mask control all depend on ALE.

---

**Next: [Chapter 6: GAAFET & Nanosheet Release](#chapter-6)**
