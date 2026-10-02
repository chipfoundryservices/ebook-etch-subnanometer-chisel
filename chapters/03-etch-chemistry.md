# Chapter 3: Etch Chemistry & Selectivity
## Fluorocarbon Chemistries and the Passivation Balancing Act

---

## 3.1 Why Fluorine?

Fluorine is the most electronegative element on the periodic table. It forms exceptionally strong bonds and has an enormous appetite for electrons.

When fluorine attacks silicon:
$$\text{Si} + \text{F}^• \rightarrow \text{SiF}$$

The reaction is violently exothermic—energy is released. The Si—F bond strength (~135 kcal/mol) is far higher than Si—Si (~52 kcal/mol) or Si—O (~110 kcal/mol).

**Why this matters for etch:**
- Fluorine radicals preferentially attack silicon
- The reaction products (SiF₂, SiF₃, SiF₄) are volatile gases—they escape the surface
- The surface is continuously refreshed for further reaction

No other element combines such high reactivity with gaseous products. This is why fluorocarbon chemistries (CF₄, C₄F₈, CHF₃, etc.) dominate semiconductor etching.

---

## 3.2 The Fluorocarbon Chemistry Family

### 3.2.1 Perfluorocarbons: CF₄, C₂F₆, C₃F₈, C₄F₈

**CF₄ (Carbon Tetrafluoride)**

Dissociation in plasma:
$$e^- + CF_4 \rightarrow CF_3^• + F^• + e^-$$
$$e^- + CF_4 \rightarrow CF_2^• + 2F^• + e^-$$
$$e^- + CF_4 \rightarrow CF^• + 3F^• + e^-$$

Products: Fluorine radicals (F•), difluoromethyl (CF₂•), trifluoromethyl (CF₃•)

**Use cases:**
- Silicon etch (high F• generation)
- High etch rates (300–1000 nm/min possible)
- Low selectivity to other materials (everything exposed to high F• flux gets attacked)

**Limitation:** Poor selectivity. CF₄ generates so many fluorine radicals that oxide, nitride, and metals all etch rapidly.

---

**C₄F₈ (Octafluorocyclobutane)**

Dissociation products: CF₂• (particularly abundant), F•, smaller CF fragments

**Key difference from CF₄:** 
- CF₂• is a large radical
- When CF₂• strikes a surface, it can form a **polymer deposit**: a film of C—F bonds
- This polymer is inert to further attack

**Use cases:**
- Selective oxide vs. nitride etch (polymer deposits preferentially on nitride)
- Controlled etch rates (polymer layer limits etch)
- 3D NAND and complex structures (selectivity is essential)

**Mechanism—Polymer Passivation:**

In C₄F₈ chemistry with silicon nitride:
1. CF₂• radicals strike the surface
2. Some react with the surface; others deposit as polymer
3. A thin (nanometer-scale) polymer layer builds up on nitride
4. Fluorine radicals cannot penetrate the polymer easily
5. Etch rate of nitride drops dramatically
6. Oxide, lacking the same polymer affinity, continues to etch

Result: Selective oxide etch with 10–20:1 selectivity to nitride.

---

**C₃F₈, C₂F₆:** Intermediate chemistries, rarely used in modern fabs.

---

### 3.2.2 Partially Fluorinated Hydrocarbons: CHF₃, CH₂F₂, C₂H₂F₄

**CHF₃ (Fluoroform)**

Dissociation:
$$e^- + CHF_3 \rightarrow CF^• + F^• + H^• + e^-$$
$$e^- + CHF_3 \rightarrow CF_2^• + F^• + H^• + e^-$$

Products: CF₂•, CF•, F•, H atoms (hydrogen is a reducing agent)

**Key property:** Hydrogen content acts as a **moderating agent**. It reduces the aggressiveness of fluorine radicals.

**Use cases:**
- Oxide and nitride etch with moderate selectivity (5–10:1)
- Metal etch (fluorine attacks the metal; hydrogen limits radical damage)
- Processes requiring less aggressive chemistry

---

## 3.3 Selectivity Mechanisms in Detail

### 3.3.1 Mechanism #1: Surface Energy / Bond Strength

Different materials have different susceptibility to radical attack:

| Material | Si—F bond | Etch susceptibility |
|----------|----------|-------------------|
| Si       | 135 kcal/mol | Very high |
| SiO₂     | Si—O: 110; Si—F: 150 | Medium–High |
| Si₃N₄    | Si—N: 105; Si—F: 150 | Low–Medium |
| SiC      | Si—C: 118 | Low |
| Metals (W, Cu) | M—F: Varies | Moderate |

A fluorine radical prefers to break weak Si—O bonds (oxide etches fast) over strong Si—N bonds (nitride etches slowly).

---

### 3.3.2 Mechanism #2: Polymer Passivation

**Definition:** Polymer passivation is the preferential deposition of a carbon-fluorine film on a particular surface.

**Physical basis:**

Different materials interact differently with CFₓ radicals:
- **Silicon:** CFₓ radicals react instantly with the silicon surface, producing SiFₓ volatiles. No polymer builds up.
- **Silicon nitride:** CFₓ radicals deposit more readily, forming a C—F polymer film.
- **Silicon oxide:** Intermediate; limited polymer deposition.

**The result:** With C₄F₈ chemistry:
- Nitride surface: covered with polymer, etches slowly
- Oxide surface: not passivated, etches normally
- Silicon: not passivated, etches very fast

This is the mechanism enabling 3D NAND etch, where alternating oxide-nitride layers must be etched with 10–20:1 selectivity.

---

### 3.3.3 Mechanism #3: Ion Bombardment Selectivity

Even without chemical differences, ion bombardment can create selectivity.

**Sputtering:** An ion with 100 eV energy can displace surface atoms through momentum transfer. Different materials have different sputtering yields.

| Material | Sputtering yield (atoms/ion) |
|----------|-----|
| Si       | 0.3–0.8 |
| SiO₂     | 0.1–0.3 |
| Si₃N₄    | 0.05–0.15 |

Higher sputtering yield = faster ion-driven etch.

This is why **low-energy ion processes** (60–100 eV) can achieve selectivity based purely on sputtering differences, without chemical differences.

---

## 3.4 The Etch Rate Versus Selectivity Trade-Off

One of the fundamental challenges in etch engineering:

$$\text{Increasing etch rate typically decreases selectivity}$$

**Why?**

Etch rate is proportional to radical flux and ion energy:
$$\text{Etch rate} \propto n_e \times V_{bias}$$

Increasing radical flux or ion energy accelerates all materials proportionally. Selectivity depends on *differences* in reactivity—if everything reacts faster, selectivity shrinks.

**Example:**

To etch oxide fast, you increase F• flux (by using CF₄ or higher power). But high F• flux attacks nitride and other materials too. Selectivity drops from 20:1 to 5:1.

To recover selectivity, you must use controlled polymer deposition (C₄F₈, lower power), which reduces overall etch rate.

**Solution:** Use a **multi-step process**:
1. **High-rate step:** Etch most of the oxide fast (CF₄, high power)
2. **Selective endpoint step:** Slow down and use C₄F₈ (high selectivity) to etch the last 50 nm, stopping precisely on nitride

Fabs use this approach extensively. A single "oxide etch" process might actually be 3–5 linked steps, each optimized for different goals.

---

## 3.5 The Fluorine-Carbon Balance

In complex fluorocarbon chemistries, etch behavior depends on the **F/C ratio**:

- **High F/C (e.g., CF₄):** Lots of fluorine, little polymer → high etch rate, low selectivity
- **Low F/C (e.g., C₄F₈):** Less fluorine, more polymer → low etch rate, high selectivity

Modern fabs adjust the **gas mixture** to tune this ratio in real-time.

**Example process:**
```
STEP 1: Etch trench (high rate)
  Gas mix: 80% CF₄ + 20% Ar
  Power: 500 W ICP + 100 W bias
  Pressure: 50 mTorr
  Duration: 2 minutes
  Etch depth: 400 nm

STEP 2: Selectivity step (protect sidewalls)
  Gas mix: 50% C₄F₈ + 50% Ar
  Power: 300 W ICP + 50 W bias
  Pressure: 20 mTorr
  Duration: 30 seconds
  Etch depth: 50 nm
  Purpose: Ensure clean nitride etch stop
```

Each step is optimized for its purpose. The complexity is vast.

---

## 3.6 Halogen Chemistries Beyond Fluorine

### 3.6.1 Chlorine Radicals (Cl•)

**Cl₂, CCl₄, BCl₃**

Chlorine is less electronegative than fluorine but still reactive.

**Use cases:**
- Metal etch (tungsten, copper, aluminum)
- Silicon etch (when fluorine selectivity is not needed)
- Polysilicon gate etch

**Advantage over fluorine:** Metal chlorides have different vapor pressures than fluorides, enabling selectivity between metals and dielectrics.

---

### 3.6.2 Bromine Radicals (Br•)

Less commonly used; intermediate between chlorine and fluorine.

---

## 3.7 Gas Mixture Strategies

Modern etch processes use **multi-component gas mixtures** to achieve precise control:

| Component | Role | Effect |
|-----------|------|--------|
| CF₄ or C₄F₈ | Active etchant | Fluorine radical source |
| Ar (Argon) | Inert gas | Sputtering ion source |
| He (Helium) | Inert gas | Low mass, fast thermal response |
| O₂ (Oxygen) | Modifier | Enhances polymer deposition in some chemistries |
| N₂ (Nitrogen) | Modifier | Reduces radical concentration, slows etch |

**Example:** 3D NAND oxide etch might use:
$$\text{60% Ar + 30% C}_4\text{F}_8 + 10% \text{CO}_2$$

Each component serves a purpose:
- **Ar:** Ions for directional etch
- **C₄F₈:** Fluorine radicals + polymer control
- **CO₂:** Oxygen-containing species to fine-tune polymer deposition

---

## 3.8 Process Integration: The Etch Sequence

In real manufacturing, a single "etch step" in the device schematic might require 5–10 plasma etch process steps:

**Example: 3nm FinFET Fin Etch**

```
STEP 1: Photoresist hardening
  Gas: He, pressure: 5 Torr, O₂ plasma
  Purpose: Cross-link resist to prevent degradation

STEP 2: Resist breakthrough
  Gas: CF₄ + Ar, bias: 300 V
  Purpose: Remove resist scum, expose silicon

STEP 3: High-rate fin etch
  Gas: CF₄ + Ar, bias: 100 V, ICP: 800 W
  Purpose: Etch 80% of fin depth fast

STEP 4: Selectivity step
  Gas: C₄F₈ + Ar, bias: 60 V, ICP: 400 W
  Purpose: Slow down, form polymer, stop precisely

STEP 5: Nitride hard mask removal
  Gas: CHF₃ + O₂, bias: 200 V
  Purpose: Etch through Si₃N₄ mask, stop on SiO₂

STEP 6: Resist strip
  Gas: O₂ plasma (no fluorine)
  Purpose: Remove remaining photoresist
```

Each step is 30 seconds to 2 minutes. Total fin etch sequence: ~20 minutes per wafer.

The fab must validate:
- Etch depth uniformity: ±2%
- Fin sidewall verticality: ±0.5°
- Undercut: < 1 nm
- Defects: < 0.1% scrap

---

## 3.9 The Tuning Problem: Process Windows

A fundamental challenge: **How narrow is the "process window"** for a given etch?

A process window is the range of parameters (power, pressure, gas flow, bias voltage) within which acceptable results are achieved.

Typical windows are surprisingly narrow:

**Oxide etch via C₄F₈:**
- Pressure: 20–30 mTorr (50% variation)
- ICP power: 300–500 W (40% variation)
- Bias power: 50–100 W (50% variation)
- C₄F₈ flow: 80–120 sccm (33% variation)

Outside these ranges, etch uniformity or selectivity degrades.

In a fab with 100+ etch chambers, maintaining all chambers within these narrow windows requires:
- Real-time plasma diagnostics
- Automatic recipe adjustment
- Preventive maintenance
- Spare parts inventory

**This is why equipment manufacturers have durable moats.** A fab customer cannot easily implement such control systems independently. They rely on Lam or Applied's expertise and service infrastructure.

---

## 3.10 Key Takeaways: Etch Chemistry

1. **Fluorine is dominant because of its reactivity and gaseous products.** Si—F bonds are easy to break; SiFₓ products are volatile.

2. **Selectivity is a surface chemistry problem.** Understanding polymer passivation, bond strengths, and ion bombardment effects is key.

3. **The F/C ratio controls the etch/selectivity trade-off.** High F/C = fast etch but poor selectivity. Low F/C = slow etch but excellent selectivity.

4. **Multi-step processes are essential.** High-rate and selective steps are often combined to achieve both speed and precision.

5. **Gas mixtures are carefully tuned.** Inert carriers (Ar, He) and modifiers (O₂, N₂) enable fine control.

6. **Process windows are narrow.** Small variations in power, pressure, or gas flow can destroy selectivity or uniformity. This is a major source of the moat for equipment suppliers.

7. **Polymer passivation is a sophisticated phenomenon.** Understanding why C₄F₈ deposits polymer on nitride but not oxide requires deep materials science knowledge.

---

**Next: [Chapter 4: The 3D NAND Miracle](#chapter-4)**
