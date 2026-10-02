# Chapter 6: GAAFET & Nanosheet Release
## Selective Silicon-Germanium Etch Without Lattice Damage

---

## 6.1 The Evolution: FinFET to Gate-All-Around

### 6.1.1 FinFET (2011–2021)

In FinFET (Fin Field-Effect Transistor), a thin silicon fin sits on top of the substrate. The gate wraps around three sides (top and two fins) of the channel.

**Architecture:**
```
        Gate
      ┌─────┐
      │     │
      │  ┌──┴──┐  Gate wraps around 3 sides
   ┌──┴──┴─┐   │
   │   Fin │   │
   │       │   │
   └───────┘   │
      └────────┘
```

**Advantages over planar transistors:**
- Improved gate control over channel
- Reduced leakage current
- Better scaling to smaller nodes

**Limitations:**
- As fins shrink (< 5 nm width), quantum confinement effects emerge
- Fin sidewall roughness becomes significant (few atoms) and affects performance
- Fin height is limited by etch anisotropy

---

### 6.1.2 Gate-All-Around (GAA) / Nanosheet Architecture

In GAA, the channel is a **thin silicon nanosheet** (3–10 nm thick) that is completely surrounded by gate dielectric and gate conductor.

**Architecture:**
```
        Gate
      ┌──────┐
      │      │
   ┌──┤      ├──┐
   │  │ Nano │  │  Gate surrounds all 4 sides
   │  │sheet │  │  (top, bottom, left, right)
   └──┤      ├──┘
      │      │
      └──────┘
```

**Advantages:**
- Better gate control (wrap-around geometry)
- Lower leakage current
- Larger effective width without increasing die area
- Scalability beyond 3 nm

**Etch Challenge:**
To form a nanosheet, sacrificial **Silicon-Germanium (Si₀.₇Ge₀.₃) layers** beneath and above must be selectively etched away, "releasing" the silicon nanosheet.

---

## 6.2 The Selectivity Problem: Si vs. SiGe

### 6.2.1 Why Si/SiGe Selectivity is Difficult

**Bond Strength Comparison:**
- Si—Si bond: 188 kcal/mol
- Si—Ge bond: ~184 kcal/mol (very similar)
- Ge—Ge bond: ~172 kcal/mol

The Si—Ge bond is *nearly as strong* as Si—Si. Chemical selectivity based on bond breaking alone cannot exceed 2–3:1.

**Conventional Fluorine Etch:**

Using CF₄ or C₄F₈ plasma:
- SiGe etch rate: ~150 nm/min
- Si etch rate: ~120 nm/min
- Selectivity: ~1.25:1 (essentially no selectivity)

If you etch the SiGe sacrificial layer (nominally 20 nm) using RIE:
- Some regions: 18 nm (under-etched)
- Other regions: 25 nm (over-etched, exposed Si underneath)

The silicon nanosheet is now damaged in some areas.

---

### 6.2.2 The ALE Solution: Selective SiGe Removal

ALE enables high selectivity through the self-limiting mechanism.

**Mechanism: Cl-Based ALE for SiGe**

**Step 1: Selective Adsorption**

Chlorine gas is introduced. Cl₂ chemisorbs to the surface.

Key observation: **Germanium is more reactive than silicon.**

- SiGe surface exposes both Ge and Si atoms
- Ge has a higher affinity for Cl
- Chlorine preferentially adsorbs on Ge-rich regions
- Si-rich regions adsorb chlorine much more slowly

**Step 2: Selective Desorption**

Low-energy Ar⁺ ions (30 eV) strike the surface.

- Ge—Cl bonds are disrupted, Ge is ejected
- Si—Cl bonds are *not* disrupted (because they formed less readily in step 1)
- The underlying Si nanosheet is untouched

**Step 3: Self-Limiting Effect**

Once the top Ge-rich layer is removed, the next layer underneath is exposed. This layer has a different Ge:Si ratio. Selectivity reorients based on the local composition.

By repeating this cycle 100–200 times (one per atomic layer), the entire 20 nm SiGe sacrificial layer is selectively removed:
- SiGe etch rate: 0.1–0.2 nm/cycle
- Si etch rate: 0.001–0.01 nm/cycle
- Selectivity: **50:1 to 100:1** (and can be tuned higher)

---

## 6.3 Process Flow: Nanosheet Release

### 6.3.1 Before ALE: The Traditional Approach

Historically (pre-2018), releasing nanosheets required creative workarounds:

**Wet Chemical Etch:**
- Immerse wafer in HCl solution
- HCl selectively attacks SiGe over Si (but selectivity is still only 3–5:1)
- Requires extremely careful control of time and temperature
- Cannot be used after gate formation (corrosive to metals)
- Very slow (~10 nm/hour)

**Isotropic RIE:**
- Use a non-selective chemistry (e.g., Cl₂ + Ar RIE)
- Etch both Si and SiGe at similar rates
- Accept poor selectivity
- Live with exposure of Si and risk of damage

---

### 6.3.2 Modern GAA Flow with ALE

**Pre-release steps:**
1. Form bottom SiGe layer (~20 nm, Si₀.₇Ge₀.₃)
2. Deposit Si nanosheet (~7 nm)
3. Deposit top SiGe layer (~20 nm)
4. Deposit hardmask (Si₃N₄)
5. Lithography and etch hardmask to create release trench pattern
6. Conventional RIE to partially release the nanosheet (etch 80% of SiGe)

**ALE Release step:**
7. **ALE SiGe removal:** Use Cl-based ALE to selectively remove remaining SiGe (20 nm × 0.1 nm/cycle = 200 cycles, ~3–5 hours)

**Post-release steps:**
8. Deposit gate dielectric (HfO₂ or equivalent)
9. Deposit gate conductor (TiN, W, etc.)
10. CMP and interconnect formation

---

## 6.4 Process Parameters and Challenges

### 6.4.1 ALE SiGe Process Parameters

| Parameter | Typical Value | Criticality |
|-----------|---|---|
| Temperature | 50–80 °C | High (thermal desorption) |
| Cl₂ pressure | 1–5 Torr | High (affects selectivity) |
| Adsorption time | 3–5 seconds | High (monolayer coverage) |
| Ion energy | 25–35 eV | Critical (selectivity vs. damage) |
| Ion dose | 5×10¹⁴ cm⁻² | Critical (complete layer removal) |
| Purge time | 3–5 seconds | Medium |
| Cycle time | ~20 seconds | Medium (process control) |

---

### 6.4.2 Selectivity Tuning

**Selectivity lever 1: Ion energy**

- Lower ion energy (20 eV): Better selectivity (weaker Ge—Cl bonds break preferentially), but slower etch
- Higher ion energy (40 eV): Faster etch, but Si damage risk increases

**Selectivity lever 2: Cl₂ pressure**

- Lower pressure (1 Torr): Less Cl adsorbs, only high-affinity sites (Ge-rich) are attacked
- Higher pressure (5 Torr): More Cl adsorbs, even Si-rich regions partially attacked

**Selectivity lever 3: Adsorption time**

- Short time (2 sec): Incomplete Cl coverage, Ge-preferential
- Long time (5 sec): Complete Cl coverage, but potentially on Si too

Fabs tune these levers to achieve the required selectivity for their specific SiGe composition.

---

## 6.5 Challenges and Defects

### 6.5.1 Incomplete Release

If selectivity is not high enough, some SiGe remains beneath the nanosheet.

**Consequence:**
- Nanosheet is not fully released
- Strain remains in the channel
- Threshold voltage is out-of-spec
- Device fails

---

### 6.5.2 Lateral Etch (Undercut)

Even with ALE, some lateral etch of the nanosheet can occur.

**Cause:**
- Radicals generated in the chamber can diffuse
- Some Cl radicals are not ion-assisted and can attack Si sidewalls
- Over many cycles, lateral etch accumulates

**Consequence:**
- Nanosheet width shrinks unexpectedly
- Channel resistance increases
- Timing is affected

**Mitigation:**
- Reduce Cl₂ pressure to suppress radical-only etch
- Increase purge time between adsorption and desorption
- Use pulse durations that minimize lateral etch

---

### 6.5.3 Ge Out-Diffusion

At elevated temperatures, Ge atoms can diffuse from the SiGe into the adjacent Si nanosheet.

**Consequence:**
- Nanosheet is no longer pure Si
- Ge—Si intermixing changes electrical properties
- Band gap, carrier mobility affected

**Mitigation:**
- Lower process temperature to < 70 °C
- Minimize ALE cycle time

---

## 6.6 Economic Impact

### 6.6.1 Process Complexity Cost

Implementing ALE-based nanosheet release adds cost:

**Capital equipment:**
- New ALE chamber: $15M
- Installation & training: $1M
- Fab must buy ALE chambers alongside conventional RIE chambers

**Operational cost:**
- ALE is slow (3–5 hours per nanosheet release)
- Fab capacity is reduced (fewer wafers per chamber per day)
- Need more ALE chambers to maintain throughput

**Training:**
- Process engineers must learn ALE
- New diagnostics and troubleshooting required
- Support cost increases

**Total added cost per GAA node:** $100M–500M in capex (for ALE chambers and infrastructure)

---

### 6.6.2 Why Adopt ALE?

Despite the cost, fabs are rapidly adopting ALE for GAA release.

**Reason: Yield.**

A conventional RIE nanosheet release process might achieve 70–80% yield (due to selectivity issues, undercut, damage).

An ALE-based release process can achieve 95%+ yield.

At $30,000 profit per wafer (advanced logic), the yield improvement generates tens of millions of dollars in additional revenue per fab per year.

The economics favor ALE adoption.

---

## 6.7 Key Takeaways: GAAFET & Nanosheet Release

1. **Gate-All-Around (GAA) is the future transistor architecture.** Complete gate wrap provides better electrostatic control and lower leakage.

2. **Nanosheet release requires selective SiGe etch.** Si/SiGe selectivity is chemically difficult; conventional etch achieves only 1.25–3:1.

3. **ALE enables high selectivity (50–100:1).** Self-limiting reactions on Ge-rich surfaces solve the selectivity problem.

4. **Chlorine-based ALE is the standard.** Ge has higher Cl affinity than Si, enabling Ge-preferential attack.

5. **Process parameters are critical and narrow.** Temperature, pressure, ion energy, and adsorption time must be tightly controlled.

6. **Lateral etch and Ge out-diffusion are key defects.** Careful process tuning minimizes these risks.

7. **ALE adoption is driven by yield economics.** Improved selectivity justifies the capital and operational costs.

8. **Nanosheet release is a leading indicator of ALE adoption.** Wherever GAA devices are manufactured, ALE chambers are deployed.

---

**Next: [Chapter 7: Equipment Engineering & Hardware Moats](#chapter-7)**
