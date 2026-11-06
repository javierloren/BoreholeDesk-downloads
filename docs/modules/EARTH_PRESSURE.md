# Earth pressure and excavation checks

[Module index](../../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Undrained cohesive earth pressure with a tension cut-off](#pressure)
- [Rankine and normally consolidated at-rest pressure](#pressure_drained)
- [Coulomb active resultant for an inclined wall and backfill](#pressure_coulomb)
- [Compare at-rest pressure hypotheses](#pressure_k0)
- [Local Rankine–Bell active pressure in layered effective-stress ground](#pressure_layered)
- [Basal bearing analogy and hydraulic plug uplift](#excavation)

<a id="pressure"></a>

## Undrained cohesive earth pressure with a tension cut-off

**Worksheet:** Cohesive earth pressure.

### Formulation

```math
\begin{gathered}
p_a(z)=\max(0,\gamma z+q-2s_u),\qquad p_p(z)=\gamma z+q+2s_u\\
z_c=\max\left(0,\frac{2s_u-q}{\gamma}\right),\qquad P_a=\int_0^H p_a(z)\,dz
\end{gathered}
```

z is depth, H retained height, γ total unit weight, q uniform surcharge and su undrained strength. The wall is vertical and smooth; the homogeneous surface is horizontal and φu=0. Tensile soil pressure is set to zero. The potential tension-crack extent is interpreted within the retained height; water in a crack requires a separate explicit action assessment. Resultants are forces per metre of wall.

### Inputs and units

| Input |
| --- |
| Retained height (m) |
| Total unit weight (kN/m3) |
| Undrained strength (kPa) |
| Uniform surcharge (kPa) |

### Outputs and application

Results include Theoretical tension crack depth (m); Active resultant (kN/m); Active lever above base (m); Passive resultant (kN/m); Passive lever above base (m).

**Application conditions:** H,gamma >0; su and surcharge >=0. Undrained total-stress Rankine screening with tension cut-off. Crack-water pressure is separate; no wall friction or inclined backfill.

**References:** [earth](BIBLIOGRAPHY.md#earth).


<a id="pressure_drained"></a>

## Rankine and normally consolidated at-rest pressure

**Worksheet:** Rankine / Jaky - dry or groundwater.

### Formulation

```math
\begin{gathered}
K_a=\frac{1-\sin\phi'}{1+\sin\phi'},\qquad K_p=\frac1{K_a},\qquad K_0=1-\sin\phi'\\
p_h(z)=K\bigl[\sigma'_v(z)+q\bigr]+u(z),\qquad u=\gamma_w\max(0,z-z_w)
\end{gathered}
```

φ′ is effective friction angle, zw groundwater depth and q uniform surcharge. σ′v is effective overburden from the entered moist/saturated unit weights. Hydrostatic u is added once, independently of K. The pressure diagrams are integrated to give total forces and application heights. Use the intended active, passive or normally consolidated at-rest state; mobilization and wall movement must suit that choice.

### Inputs and units

| Input |
| --- |
| Retained height (m) |
| Effective friction angle (degrees) |
| Unit weight above water (kN/m3) |
| Saturated unit weight (kN/m3) |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Uniform surcharge (kPa) |

### Outputs and application

Results include Active coefficient; Active total force (kN/m); Active lever above base (m); Active soil force (kN/m); Active surcharge force (kN/m); At rest coefficient; At rest total force (kN/m); At rest lever above base (m); At rest soil force (kN/m); At rest surcharge force (kN/m); Passive coefficient; Passive total force (kN/m); Passive lever above base (m); Passive soil force (kN/m); Passive surcharge force (kN/m); Hydrostatic force component (kN/m).

**Application conditions:** H,gamma >0; 0 <= phi <60 deg; surcharge >=0; water depth >=0 or blank=dry. In wet ground gamma_sat > gamma_water >0. Rankine level ground/smooth wall; Jaky K0 assumes normally consolidated ground.

**References:** [earth](BIBLIOGRAPHY.md#earth).


<a id="pressure_coulomb"></a>

## Coulomb active resultant for an inclined wall and backfill

**Worksheet:** Coulomb active - dry inclined wall/backfill.

### Formulation

```math
\begin{gathered}
K_a=\frac{\sin^2(\alpha+\phi')}{\sin^2\alpha\sin(\alpha-\delta)\left[1+\sqrt{\frac{\sin(\phi'+\delta)\sin(\phi'-\beta)}{\sin(\alpha-\delta)\sin(\alpha+\beta)}}\right]^2}\\
P_a=\frac12K_a\gamma H^2+K_aqH\frac{\sin\alpha\cos\beta}{\sin(\alpha+\beta)}
\end{gathered}
```

α is the wall angle to horizontal (90° vertical), β the upslope ground angle, δ wall friction and φ′ soil friction. q is vertical surcharge per horizontal area. The wall-head coordinates relative to the toe are (−H cotα,H), defining the implemented angle convention. Pa is a resultant: Ph=Pa sin(α−δ) and downward Pv=Pa cos(α−δ). Soil and surcharge parts act at H/3 and H/2 above the toe respectively. Use dry/moist homogeneous cohesionless ground.

### Inputs and units

| Input |
| --- |
| Vertical retained height H (m) |
| Dry/moist unit weight (kN/m3) |
| Effective friction angle (deg) |
| Wall angle alpha (deg; vertical=90) |
| Backfill upslope angle beta (deg) |
| Wall friction delta (deg) |
| Vertical surcharge per HORIZONTAL area (kPa) |

### Outputs and application

Results include Coulomb resultant coefficient Ka; Horizontal coefficient; Soil resultant (kN/m); Surcharge resultant (kN/m); Total resultant (kN/m); Horizontal thrust magnitude (kN/m); Vertical force downward positive (kN/m); Resultant height above toe (m).

**Application conditions:** Dry homogeneous cohesionless active wedge; H,gamma>0; q>=0 per horizontal area; 0<=phi<60; 60<=alpha<=120; 0<=delta<=phi; 0<=beta<phi or beta=phi=0. No passive resistance, water or seismic.

**References:** [coulomb](BIBLIOGRAPHY.md#coulomb).


<a id="pressure_k0"></a>

## Compare at-rest pressure hypotheses

**Worksheet:** At rest - Jaky / OCR / elastic comparison.

### Formulation

```math
K_{0,NC}=1-\sin\phi',\quad K_{0,OCR}=(1-\sin\phi')OCR^{\sin\phi'},\quad K_{0,elastic}=\frac{\nu}{1-\nu}
```

OCR is overconsolidation ratio and ν the elastic Poisson ratio. The three coefficients represent distinct hypotheses, not safety factors or automatically interchangeable design alternatives. Each coefficient acts on effective overburden plus the entered surcharge; hydrostatic water pressure is added once. The worksheet integrates each profile and reports forces and levers. Adopt the hypothesis consistent with ground history and restraint.

### Inputs and units

| Input |
| --- |
| Retained height (m) |
| Effective friction angle (degrees) |
| Unit weight above water (kN/m3) |
| Saturated unit weight (kN/m3) |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Uniform surcharge (kPa) |
| Overconsolidation ratio OCR |
| Elastic Poisson ratio nu |

### Outputs and application

Results include Jaky NC K0; Jaky NC total force (kN/m); Jaky NC lever above base (m); Mayne-Kulhawy OCR K0; Mayne-Kulhawy OCR total force (kN/m); Mayne-Kulhawy OCR lever above base (m); Elastic constrained K0; Elastic constrained total force (kN/m); Elastic constrained lever above base (m).

**Application conditions:** Homogeneous horizontal retained ground; OCR>=1; 0<=nu<0.5; 0<=phi<60. Compare Jaky NC, OCR correlation and constrained elasticity as distinct hypotheses. Water added once, no flow or compaction.

**References:** [at_rest](BIBLIOGRAPHY.md#at_rest).


<a id="pressure_layered"></a>

## Local Rankine–Bell active pressure in layered effective-stress ground

**Worksheet:** Rankine-Bell active - layered effective stresses.

### Formulation

```math
p_a(z)=\max\left[0,K_{a,j}\sigma'_v(z)-2c'_j\sqrt{K_{a,j}}\right]+u(z),\qquad K_{a,j}=\frac{1-\sin\phi'_j}{1+\sin\phi'_j}
```

j identifies the material at depth z. Effective vertical stress includes surcharge and all overlying layer weights. Layer boundaries, water level and tension transitions are integrated as piecewise pressure segments; boundary jumps are retained. Use contiguous horizontal strata, a smooth vertical wall and the shared hydrostatic water level. The summed tension-zone thickness is a local pressure diagnostic, not necessarily a connected field crack. The c′=0 sensitivity calculation helps assess reliance on the adopted cohesion.

### Inputs and units

| Input |
| --- |
| Retained height (m) |
| Uniform surcharge (kPa) |
| Water depth (m; blank=dry) |
| Water unit weight (kN/m3) |

**Layers table:** Top depth (m); Bottom depth (m); Moist unit weight (kN/m3); Saturated unit weight (kN/m3); Effective friction angle (deg); Effective cohesion (kPa).


### Outputs and application

Results include Total active force (kN/m); Moment about base (kN m/m); Resultant height above base (m); c=0 sensitivity force (kN/m); Sum of tensile-zone thicknesses (m).

**Application conditions:** Vertical smooth wall, horizontal contiguous layers covering 0..H; 1..100 layers. H,gamma>0; gamma_sat>gamma_water>0; c,q>=0; 0<=phi<60. Hydrostatic water only. Local pressure approximation, not global wedge equilibrium. No passive, seismic, seepage, compaction or independent perched crack-water model.

**References:** [earth](BIBLIOGRAPHY.md#earth).


<a id="excavation"></a>

## Basal bearing analogy and hydraulic plug uplift

**Worksheet:** Excavation screening checks.

### Formulation

```math
F_{base}=\frac{N_c s_u}{\gamma H+q},\qquad F_{uplift}=\frac{\gamma_{plug}h}{\gamma_w H_w}
```

H is excavation depth, su the selected undrained strength, Nc an adopted basal factor and q surcharge. For uplift, h is impermeable plug thickness, γplug its total unit weight, and Hw the pressure head at its underside with zero upper-face water pressure. The two checks can be supplied separately. Geometry, confinement and hydraulic boundary conditions must justify the selected simplification; uplift is not a piping calculation.

### Inputs and units

| Input |
| --- |
| Excavation depth (m) |
| Overburden unit weight (kN/m3) |
| Undrained strength (kPa) |
| Selected basal Nc |
| Surcharge (kPa) |
| Impermeable plug thickness (m) |
| Plug total unit weight (kN/m3) |
| Pressure head at plug underside (m) |
| Water unit weight (kN/m3) |
| Target uplift safety factor |

### Outputs and application

Results include Basal driving stress (kPa); Basal resistance (kPa); Basal heave resistance / demand; Plug resisting stress (kPa); Uplift pressure (kPa); Hydraulic uplift safety factor; Required plug thickness (m).

**Application conditions:** Complete either basal or uplift input group. H,gamma,su,Nc,plug thickness/weight,water weight and pressure head >0; surcharge >=0; target FS >=1. Simplified basal and uplift checks; no universal safe excavation depth.

**References:** [earth](BIBLIOGRAPHY.md#earth), [gec6](BIBLIOGRAPHY.md#gec6).
