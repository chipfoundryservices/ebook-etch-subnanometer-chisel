# Appendix A: Mathematical Derivations

---

## A.1 Self-Bias Voltage in Capacitively Coupled Plasma (CCP)

### Derivation of DC Self-Bias

**Setup:**
- Upper electrode (powered): area $A$, driven at RF voltage $V_{RF}$
- Lower electrode (wafer): area $A$, grounded
- Plasma gap: distance $d$

**Key insight:** Electrons are much lighter than ions and respond faster to RF oscillation.

**In one RF cycle:**
- Electrons oscillate over displacement $\Delta x_e$
- Ions barely move: $\Delta x_i \approx 0$ (due to inertia)

Net result: Electrons accumulate near lower electrode (wafer), creating negative DC bias.

**Quantitative derivation:**

The peak ion current to the wafer is proportional to:
$$J_i \propto n_e \sqrt{\frac{eT_e}{m_i}}$$

where $T_e$ is electron temperature and $m_i$ is ion mass.

The peak electron current leaving the wafer is:
$$J_e \propto n_e \sqrt{\frac{eT_e}{2\pi m_e}}$$

**Current balance:** Over a complete RF cycle, currents must balance on average:
$$\bar{J}_i = \bar{J}_e$$

However, electrons can only leave the wafer if they have sufficient energy to overcome potential barrier $V_{bias}$.

**Richardson equation (thermionic emission analog):**
$$J_e \propto \exp\left(-\frac{eV_{bias}}{kT_e}\right)$$

**Self-consistent solution:**

Matching ion and electron currents:

$$n_e \sqrt{\frac{eT_e}{m_i}} \approx n_e \sqrt{\frac{eT_e}{2\pi m_e}} \exp\left(-\frac{eV_{bias}}{kT_e}\right)$$

Taking logarithm and solving:

$$\frac{eV_{bias}}{kT_e} = \ln\left(\sqrt{\frac{m_i}{2\pi m_e}}\right)$$

$$V_{bias} = \frac{kT_e}{e} \ln\left(\sqrt{\frac{m_i}{2\pi m_e}}\right)$$

**For Ar⁺ ions** ($m_i = 40$ amu) and $T_e = 2$ eV:

$$V_{bias} = 2 \ln\left(\sqrt{\frac{40 \times 1840}{2\pi}}\right) \approx 2 \times 5.65 \approx 11.3 \text{ V}$$

**For RF-driven system**, the applied RF voltage $V_{RF}$ couples to the plasma via capacitor. Empirically:

$$V_{bias} \approx -0.5 \sqrt{\frac{m_i}{m_e}} V_{RF}$$

For $m_i/m_e = 73,000$ (Ar) and $V_{RF} = 500$ V:

$$|V_{bias}| \approx 0.5 \times 270 \times 500 \approx 67,500 \text{ V}$$

This is an overestimate (actual values are 1–3 kV); the factor accounts for geometric and plasma-dependent corrections.

---

## A.2 Ion Sheath Thickness: Child-Langmuir Law

### Derivation

**Setup:**
- Sheath extends from plasma (potential $V_p$) to electrode (potential $V_e$)
- Voltage drop: $V_s = V_p - V_e$
- Assume sheath contains only ions and negligible electrons (depletion approximation)

**Governing equations:**

Poisson equation (1D):
$$\frac{d^2V}{dx^2} = -\frac{\rho(x)}{\epsilon_0} = -\frac{n_i(x) e}{\epsilon_0}$$

where $n_i(x)$ is ion density.

**Conservation of ion current:**

The ion current $J$ is constant throughout sheath (steady state):
$$J = n_i(x) v_i(x) e$$

where $v_i(x)$ is ion velocity.

**Energy conservation:**

An ion starting at rest in plasma (position $x=0$) accelerates:
$$\frac{1}{2}m_i v_i^2 = e(V_p - V(x)) = e V(x)$$

where we set $V_p = 0$ (plasma potential as reference).

$$v_i(x) = \sqrt{\frac{2eV(x)}{m_i}}$$

**Substituting into current equation:**

$$J = n_i(x) \sqrt{\frac{2eV(x)}{m_i}} e$$

$$n_i(x) = \frac{J}{e} \sqrt{\frac{m_i}{2eV(x)}}$$

**Substituting into Poisson:**

$$\frac{d^2V}{dx^2} = -\frac{J}{e\epsilon_0} \sqrt{\frac{m_i}{2eV(x)}}$$

**Solution (boundary conditions):**

- At $x=0$ (plasma edge): $V(0) = 0$, $\frac{dV}{dx} = 0$
- At $x=d_{sheath}$ (electrode): $V(d_{sheath}) = -V_s$

**Integration yields:**

$$d_{sheath} = \left(\frac{\pi \epsilon_0}{4}\right) \sqrt{\frac{2m_i}{e}} \frac{V_s^{3/4}}{\sqrt{J}}$$

**In terms of plasma density** (current density $J = n_e e v_i(V_s)$ at sheath edge):

$$d_{sheath} \approx \left(\frac{\pi \epsilon_0 e}{4 n_e}\right)^{1/2} V_s^{3/4}$$

**Numerical example:**

- $n_e = 10^{11}$ cm⁻³ = $10^{17}$ m⁻³
- $V_s = 300$ V
- $\epsilon_0 = 8.854 \times 10^{-12}$ F/m

$$d_{sheath} = \sqrt{\frac{\pi \times 8.854 \times 10^{-12} \times 1.6 \times 10^{-19}}{4 \times 10^{17}}} \times 300^{3/4}$$

$$d_{sheath} \approx 0.9 \times 10^{-3} \text{ m} = 0.9 \text{ mm}$$

---

## A.3 Etch Rate as Function of Radical Flux and Ion Energy

### Semi-Empirical Model

**Total etch rate:**

$$E_{total} = E_{rad} + E_{ion}$$

where:
- $E_{rad}$ = etch rate from radical (chemical) attack
- $E_{ion}$ = etch rate from ion-enhanced sputtering

**Radical etch (first-order reaction):**

$$E_{rad} = k_{rad} \Phi_{rad}$$

where $\Phi_{rad}$ is radical flux and $k_{rad}$ is reaction probability (0–1).

Radical flux is proportional to plasma density and gas flow:

$$\Phi_{rad} \propto n_e P$$

where $P$ is gas pressure.

**Ion-enhanced etch:**

The sputtering yield $Y$ depends on ion energy:

$$Y(E_{ion}) \approx Y_0 \left(E_{ion} - E_{th}\right)$$

where $E_{th}$ is threshold energy (~20 eV for most materials).

Etch rate from sputtering:

$$E_{ion} = k_{spu} Y(E_{ion}) \Phi_{ion}$$

where $\Phi_{ion}$ is ion flux.

Ion flux is:

$$\Phi_{ion} \propto n_e P_{bias}$$

where $P_{bias}$ is RF bias power.

**Combined etch rate:**

$$E_{total} \propto n_e P + P_{bias} [E_{bias} - E_{th}]$$

**Key insight:** Increasing either plasma density ($n_e$) or bias power ($P_{bias}$) increases etch rate, but in different ways:
- Plasma density increases both radical and ion etch
- Bias power increases only ion etch (but amplifies it)

---

## A.4 Selectivity from Sputtering Yield Differences

### Model

**Two materials, A and B:**

Sputtering yields:
$$Y_A(E) = Y_{A0}(E - E_{th,A})$$
$$Y_B(E) = Y_{B0}(E - E_{th,B})$$

**Etch rates:**

$$E_A = k Y_A(E) \Phi_{ion}$$
$$E_B = k Y_B(E) \Phi_{ion}$$

**Selectivity:**

$$S_{A/B} = \frac{E_A}{E_B} = \frac{Y_{A0}(E - E_{th,A})}{Y_{B0}(E - E_{th,B})}$$

**Example: Si vs. SiO₂**

- $Y_{Si,0} \approx 0.8$ atoms/ion, $E_{th,Si} \approx 20$ eV
- $Y_{SiO2,0} \approx 0.2$ atoms/ion, $E_{th,SiO2} \approx 25$ eV

At ion energy $E = 100$ eV:

$$S_{Si/SiO2} = \frac{0.8 \times (100-20)}{0.2 \times (100-25)} = \frac{64}{15} \approx 4.3:1$$

At lower ion energy $E = 50$ eV:

$$S_{Si/SiO2} = \frac{0.8 \times (50-20)}{0.2 \times (50-25)} = \frac{24}{5} = 4.8:1$$

Selectivity is relatively insensitive to ion energy in this range—both materials etch, just at different rates.

---

## A.5 ALE Cycle Time Scaling

### First-Principles Estimate

**Single ALE cycle:**

1. **Adsorption phase:** Time $t_{ads}$
   - Reactant pressure: $P$
   - Molecular flux to surface: $\Phi_{mol} = \frac{P}{\sqrt{2\pi m_{mol} k T}}$
   - Time to monolayer saturation: $t_{ads} \sim \frac{1}{S \Phi_{mol}}$
   
   where $S$ is sticking coefficient (fraction of molecules that stick).

2. **Desorption phase:** Time $t_{des}$
   - Ion flux: $\Phi_{ion}$
   - Number of surface sites: $N_s \sim 10^{15}$ sites/cm²
   - Time to clear monolayer: $t_{des} \sim \frac{N_s}{\Phi_{ion}}$

3. **Purge phase:** Time $t_{purge}$ (typically 2–5 sec)

**Total cycle time:**

$$t_{cycle} = t_{ads} + t_{des} + t_{purge}$$

**Typical values:**

- $t_{ads} \sim 3$ sec (monolayer sticking + saturation)
- $t_{des} \sim 5$ sec (ion removal)
- $t_{purge} \sim 3$ sec
- **Total: ~11–15 sec per cycle**

**Etch depth:** ~0.1–0.2 nm per cycle

**Time to etch 20 nm layer:** $\frac{20}{0.15} \times 15$ sec = 2000 sec ≈ 33 minutes

This matches observed ALE times in practice.

---

## A.6 Polymer Passivation Layer Growth

### Reaction Model

**Step 1: CF₂ radical adsorption**

$$\text{Surface} + \text{CF}_2 \rightarrow \text{Surface-CF}_2$$

Rate: $r_1 = k_1 [\text{CF}_2]$

**Step 2: Polymer chain growth**

$$\text{Surface-CF}_2 + \text{CF}_2 \rightarrow \text{Surface-(CF}_2)_2$$

Rate: $r_2 = k_2 [\text{CF}_2][\text{Surface sites}]$

**Step 3: Ion sputtering (removal)**

$$\text{Surface-polymer} + \text{Ion} \rightarrow \text{Ion-induced removal}$$

Rate: $r_3 = k_3 \Phi_{ion}$

**Net deposition rate:**

$$\frac{d[\text{polymer}]}{dt} = r_1 + r_2 - r_3$$

$$\frac{d[\text{polymer}]}{dt} = k_1[\text{CF}_2] + k_2[\text{CF}_2][\text{sites}] - k_3\Phi_{ion}$$

**Steady state** (when $\frac{d[\text{polymer}]}{dt} = 0$):

$$[\text{polymer}]_{ss} = \frac{(k_1 + k_2[\text{sites}])[\text{CF}_2]}{k_3\Phi_{ion}}$$

**Interpretation:**

- Higher $\text{CF}_2$ or lower $\Phi_{ion}$ → thicker polymer layer
- Higher $\Phi_{ion}$ → thinner or no polymer

This explains why C₄F₈ (high CF₂ generation) with low bias power creates polymer passivation layer.

---

## A.7 Etch Uniformity: Wafer-Scale Analysis

### Microloading Effect

**Feature density variation:**

Local feature density $\rho(x,y)$ varies across wafer.

**Radical depletion:**

In high-density regions, radicals are consumed faster than replenished. Local radical flux decreases:

$$\Phi_{rad}(x,y) = \Phi_{0} e^{-k \rho(x,y)}$$

**Etch rate variation:**

$$E(x,y) = E_0 e^{-k \rho(x,y)}$$

**Uniformity:**

For $\Delta \rho = \rho_{max} - \rho_{min}$:

$$\frac{\Delta E}{E_0} = \left(1 - e^{-k\Delta\rho}\right) \approx k \Delta\rho$$

Example: $k = 0.01$ mm⁻², $\Delta\rho = 20\%$ → $\Delta E/E_0 \approx 0.2$ or 20% uniformity variation.

**Mitigation:**

- Increase gas pressure (replenish radicals faster)
- Decrease etch time (less depletion accumulation)
- Use high ion energy (reduce chemical etch, rely on ion sputtering which is less depleted)

---

## A.8 Key Formulas Summary

| Quantity | Formula | Typical Value |
|----------|---------|---|
| **Self-bias voltage** | $V_b \approx 0.5\sqrt{m_i/m_e} V_{RF}$ | -1–3 kV |
| **Sheath thickness** | $d_s \approx \left(\frac{\pi\epsilon_0 e}{4n_e}\right)^{1/2} V_s^{3/4}$ | 0.1–1 mm |
| **Ion sheath potential** | $E_{ion} = e V_s$ | 50–300 eV |
| **Etch rate (radical)** | $E_{rad} = k \Phi_{rad}$ | 50–200 nm/min |
| **Etch rate (sputtering)** | $E_{sp} = k Y(E)\Phi_{ion}$ | 20–100 nm/min |
| **Sputtering yield** | $Y(E) = Y_0(E-E_{th})$ | 0.1–1 atoms/ion |
| **Selectivity** | $S = E_A / E_B$ | 5:1–100:1 |
| **Sheath voltage** | $\phi_s = V_{bias}$ | 100–1000 V |

---

**See also:** Glossary (Appendix), Equipment Specifications (Appendix B)
