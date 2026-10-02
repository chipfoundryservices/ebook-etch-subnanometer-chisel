# Chapter 2: Plasma Physics in the Vacuum Chamber
## Capacitively Coupled Plasma vs. Inductively Coupled Plasma

---

## 2.1 Plasma: The Fourth State of Matter

**Definition:** A plasma is a quasi-neutral collection of ions, electrons, and neutral molecules in which charged species move freely. It exhibits collective behavior—the motion of one charged particle influences others.

In a semiconductor etch chamber, plasma is created by applying radiofrequency (RF) power to a gas at low pressure. The result is a glowing, ionized gas that is neither a solid, liquid, nor ordinary gas.

**Key properties:**
- **Electron temperature** ($T_e$): typically 20,000 K (2 eV, where 1 eV ≈ 11,600 K)
- **Ion temperature** ($T_i$): much lower, typically 300–1000 K (room temperature to warm)
- **Electron density** ($n_e$): typically $10^{10}$ to $10^{12}$ cm⁻³
- **Ion density** ($n_i$): approximately equal to electron density (quasi-neutrality)
- **Pressure:** typically 10–500 mTorr (much lower than atmospheric)

This asymmetry—hot electrons, cold ions—is the foundation of etching.

---

## 2.2 The Collision Cascade: How Plasma Ignites

When RF power is applied to a gas at low pressure:

### Step 1: Seed Electrons
A tiny number of free electrons exist in the chamber (from cosmic rays, radioactive decay, or prior ionization). An RF electric field accelerates these electrons.

### Step 2: Ionization Collisions
An accelerated electron collides with a neutral molecule. If the electron's kinetic energy exceeds the ionization potential (e.g., 12.6 eV for SF₆), the collision ionizes the molecule:

$$e^- + SF_6 \rightarrow 2e^- + SF_6^+$$

Now there are two electrons. Each can be accelerated and collide again.

### Step 3: Avalanche
This process repeats: electrons multiply exponentially. Within microseconds, the chamber transitions from a neutral gas to a plasma containing trillions of charged particles.

### Step 4: Equilibrium
Eventually, ionization is balanced by recombination:
- Electrons recombine with ions: $e^- + SF_6^+ \rightarrow SF_6 + \text{energy}$
- Radicals recombine with each other: $F^• + F^• \rightarrow F_2$

The plasma reaches a steady state where ionization rate equals recombination rate, maintaining a constant density of ions, electrons, and radicals.

---

## 2.3 Capacitively Coupled Plasma (CCP): The Classical Design

### 2.3.1 The Basic Architecture

A parallel-plate capacitor configuration:

```
┌─────────────────────────────┐
│  Upper electrode (RF power) │  13.56 MHz or 400 kHz
│  A = 500 cm² (example)      │
├─────────────────────────────┤
│                             │
│      PLASMA (glowing)       │  ~ 500 mTorr, ~10 cm gap
│                             │
├─────────────────────────────┤
│  Lower electrode            │  (wafer sits here)
│  (grounded)                 │
└─────────────────────────────┘
```

**How it works:**
1. RF power (typically 13.56 MHz, 500–2000 W) drives current through the upper electrode
2. Capacitive displacement current flows through the plasma
3. Electrons in the plasma are pushed downward (toward positive electrode)
4. Ions are pushed upward (toward negative electrode)
5. A **DC bias voltage** emerges—the plasma self-biases negative at the wafer

### 2.3.2 The DC Bias and Sheath

The self-bias is a consequence of electron mobility:

**Physical Reason:** Electrons are much lighter than ions (9.1 × 10⁻³¹ kg vs. ~10⁻²⁶ kg). They respond much faster to the AC electric field. In one RF cycle:
- Electrons oscillate vigorously
- Ions barely move

The net result: electrons accumulate near the wafer (lower electrode), creating a negative DC bias.

**Quantitative Result:**

The DC self-bias is approximately:

$$V_{bias} \approx -0.5 \sqrt{\frac{M_i}{m_e}} \cdot V_{RF}$$

where $M_i$ is ion mass, $m_e$ is electron mass, and $V_{RF}$ is the RF voltage amplitude.

For an Ar⁺ ion (M ≈ 40 amu) and typical RF of 500 V:

$$V_{bias} \approx -0.5 \sqrt{\frac{40 \times 1840}{1}} \cdot 500 \approx -3000 \text{ V}$$

A 3 kV DC bias accelerates ions toward the wafer to kinetic energy of 3000 eV.

### 2.3.3 Ion Sheath Physics

Just above the wafer, a thin region (sheath) forms where:
- Positive ions predominate (electrons cannot penetrate due to the potential barrier)
- Electric field is strong (~100 V/mm)
- Ions are accelerated by this field

**Sheath thickness (Child-Langmuir law):**

$$d_{sheath} \approx \left( \frac{\pi \epsilon_0 e}{4 n_e} \right)^{1/2} V_{bias}^{3/4}$$

For typical parameters:
- $n_e = 10^{11}$ cm⁻³
- $V_{bias} = 300$ V

$$d_{sheath} \approx 1 \text{ mm}$$

The sheath is thin (millimeter-scale) but contains most of the voltage drop.

### 2.3.4 Ion Bombardment Energy

Ions accelerated through the sheath gain kinetic energy equal to the sheath potential:

$$E_{ion} = e \cdot V_{sheath} \approx 50\text{–}300 \text{ eV (typical)}$$

This is the energy available to break chemical bonds at the wafer surface. It is *directional*—ions come from above, creating vertical etch.

---

## 2.4 Inductively Coupled Plasma (ICP): The Modern Approach

### 2.4.1 The Architecture

ICP uses a different coupling mechanism:

```
         RF coil (external)
         ~~~~~~~~~~~~~~~~
        ╱    ╱    ╱    ╱ 
       ╱    ╱    ╱    ╱
      ┌──────────────────┐
      │   Dielectric     │
      │   chamber wall   │
      ├──────────────────┤
      │      PLASMA      │  High density
      │   (very bright)  │  ~10¹² cm⁻³
      ├──────────────────┤
      │  Lower electrode │  (wafer)
      │  (separate bias) │  Independent RF power
      └──────────────────┘
```

**How it works:**
1. An RF coil (13.56 MHz) is wound *outside* the chamber wall
2. A time-varying magnetic field penetrates the dielectric wall
3. This magnetic field induces an electric field in the plasma (via Faraday's law)
4. The induced electric field ionizes gas molecules
5. Plasma density is very high (~10¹² cm⁻³), much higher than CCP

**Advantage:** Plasma source (inductive coil) and ion energy (bias electrode) are decoupled.

### 2.4.2 Decoupling Ion Energy from Plasma Density

In CCP, the RF power serves dual roles:
- Creates and maintains plasma
- Accelerates ions

If you increase RF power, *both* plasma density and ion energy increase. You cannot control them independently.

In ICP:
- **Inductive coil power** → controls plasma density (more power = higher density)
- **Bias electrode power** → controls ion energy (higher bias = higher energy)

This decoupling is revolutionary. You can have:
- High plasma density (fast chemical etch from radicals)
- Low ion energy (minimal charge damage)

CCP chambers cannot achieve this combination.

### 2.4.3 Dual-Frequency Bias

Advanced ICP systems (used from 2010s onward) employ **dual-frequency bias**:

- **High frequency (13.56 MHz):** Penetrates the ion sheath, controls average ion energy
- **Low frequency (400 kHz or 2 MHz):** Does not penetrate sheath, controls ion energy *distribution*

By tuning the ratio of high-frequency to low-frequency power, engineers can control:
- Average ion energy: 50–300 eV
- Ion energy *spread*: narrow vs. broad distribution

A narrow distribution (all ions at ~100 eV) gives precise etching. A broad distribution (ions at 50–200 eV) is useful for certain processes.

---

## 2.5 Plasma Chemistry: Radicals, Ions, and Selectivity

### 2.5.1 Radical Generation

When an electron collides with a molecule, it can cause:

1. **Ionization:** $e^- + CF_4 \rightarrow CF_4^+ + 2e^-$ (creates ion)
2. **Excitation:** $e^- + CF_4 \rightarrow CF_4^* + e^-$ (molecule enters excited state, then decays)
3. **Dissociation:** $e^- + CF_4 \rightarrow CF_3 + F + e^-$ (breaks into radicals)

Radicals like $F^•$, $CF_3^•$, and $CF^•$ are highly reactive—they have unpaired electrons and readily attack silicon, oxide, or other materials.

### 2.5.2 Ion vs. Radical Contribution

In modern etch chambers:
- **Radical etch** (chemical, non-directional): 60–80% of etch rate
- **Ion-enhanced etch** (sputtering + chemistry): 20–40% of etch rate

**Ion-enhanced etch mechanism:**
1. An ion strikes the surface with 100 eV energy
2. The ion displaces atoms in the top few layers, creating a "wounded" surface
3. Radicals attack these weakened bonds preferentially
4. Etch rate is boosted

This is why etch rate depends strongly on ion energy and ion flux—not just on radical chemistry.

### 2.5.3 Selectivity: The Art of Not Etching What You Don't Want

**Definition:** Selectivity is the ratio of etch rates for two materials.

$$\text{Selectivity} = \frac{\text{Etch rate of material A}}{\text{Etch rate of material B}}$$

Example: Silicon oxide (SiO₂) etch at 200 nm/min, with silicon (Si) etch at 10 nm/min:
$$\text{Selectivity} = 200/10 = 20:1$$

Achieving high selectivity requires **understanding the surface chemistry**:

For SiO₂ vs. Si etch:
- SiO₂ bonds (Si—O—Si) are weaker than Si—Si bonds
- Fluorine radicals preferentially attack the weaker bond
- The SiO₂ surface also forms a "fluoro-passivation" layer under certain conditions
- Si surface does *not* form this layer as readily
- Result: selective SiO₂ etch

For SiO₂ vs. SiN etch:
- Nitride (Si—N) bonds are actually stronger than oxide (Si—O) bonds
- But nitride surfaces interact differently with fluorocarbon radicals
- With proper chemistry (e.g., C₄F₈ rather than CF₄), a **polymer passivation layer** forms preferentially on nitride
- Oxide underneath still etches
- Result: selective oxide etch with nitride etch suppressed (selectivity 10–20:1)

**Industrial Example:** In 3D NAND stacks, dozens of alternating oxide-nitride layers must be etched. A complex etch sequence is used:
1. **First etch:** Remove oxide, *stop* on nitride (selectivity 20:1 or better)
2. **Second etch:** Remove nitride, *stop* on oxide (selectivity 10:1)
3. Repeat for 64–128 layers

Manufacturers that perfect these selectivity windows capture entire technology nodes.

---

## 2.6 Plasma Diagnostics: Measuring the Invisible

Plasma engineers use non-invasive techniques to measure plasma properties:

### 2.6.1 Langmuir Probes

A thin wire inserted into plasma collects current. By varying the probe voltage and measuring current, engineers determine:
- Plasma potential ($V_p$)
- Electron temperature ($T_e$)
- Electron density ($n_e$)

### 2.6.2 Optical Emission Spectroscopy (OES)

Light emitted by excited atoms/radicals is analyzed. Each element emits characteristic wavelengths. By measuring intensity at specific wavelengths:
- Identify which radicals are present (F, Cl, Ar, etc.)
- Infer their abundance
- Monitor plasma chemistry in real-time

### 2.6.3 RF Impedance Monitoring

The plasma acts as a resistive/capacitive load. By measuring the impedance seen by the RF generator, engineers can detect:
- Pressure changes
- Contamination or chamber wall buildup
- Plasma density shifts

### 2.6.4 Mass Spectrometry

A mass spectrometer samples ions/radicals and measures their mass-to-charge ratio, identifying what species are present and in what quantities.

---

## 2.7 The Economics of Plasma Engineering

Why can Lam Research and Applied Materials sustain such high margins?

### 2.7.1 The Complexity Barrier

A modern etch chamber contains:
- **RF power supplies:** $50K–200K (13.56 MHz + 400 kHz dual-frequency)
- **Vacuum system:** $100K–300K (turbo pump, mass flow controller, gauges)
- **Chamber vessel:** $50K–150K (stainless steel, engineering)
- **Electrode materials:** $20K–100K (yttrium oxide coatings, electrostatic chucks)
- **Gas distribution system:** $30K–80K (precision mass flow controllers)
- **Cooling system:** $20K–50K (cryogenic pumping, water chiller)
- **Control electronics:** $50K–200K (PLC, RF matching network, sensors)

**Total bill of materials: $300K–1.1M**

For a $10M equipment selling price, the BOM is only 3–11% of revenue. Gross margin is enormous.

But the **engineering, testing, and service costs** are what truly create the moat:
- Process development: 10–20 person-years per node
- Customer support: 2–3 dedicated engineers per fab (100+ fabs per supplier)
- Service parts inventory: millions per year

Only Lam and Applied can absorb these costs and still achieve profitability.

### 2.7.2 Technology Lock-In

A fab that buys a Lam chamber must:
- Train operators on Lam's user interface
- Develop recipes in Lam's process computer
- Stock Lam's spare parts
- Contract with Lam for service

Switching to Applied Materials means retraining, re-qualifying, and repurchasing. Cost: $50M+ per fab.

This switching cost is the ultimate moat.

---

## 2.8 Key Takeaways: Plasma Physics

1. **Plasma is a non-equilibrium system.** Electrons are hot (~20,000 K), ions are cold (~300 K). This asymmetry enables etch.

2. **CCP is simple but limited.** Dual-role RF power (ignition + acceleration) prevents independent control of plasma density and ion energy.

3. **ICP is complex but powerful.** Decoupled ion/plasma sources allow independent control, enabling low-damage high-selectivity etch.

4. **Dual-frequency bias is the modern standard.** Separate 13.56 MHz and 400 kHz bias frequencies control ion energy distribution.

5. **Selectivity is a surface chemistry problem.** Understanding why one material etches faster than another requires molecular-level understanding of radical attack, passivation layers, and bond strengths.

6. **Plasma diagnostics are essential.** Measuring what you cannot see (electron temperature, radical species, plasma potential) is how fabs optimize recipes.

7. **Complexity = competitive moat.** The sheer engineering complexity of modern plasma systems ensures only two major suppliers can compete globally.

---

**Next: [Chapter 3: Etch Chemistry & Selectivity](#chapter-3)**
