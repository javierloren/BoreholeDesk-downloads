# Shallow foundations and settlement

[Module index](../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Undrained footing resistance with biaxial eccentricity](#bearing)
- [General-shear footing resistance using effective stresses](#bearing_drained)
- [Uniaxial compression-only footing contact](#footing_contact)
- [Compare supplied pressures and observed or supplied settlements](#foundation_service)
- [Stress increments and one-dimensional primary consolidation](#settlement)
- [Plan and section views of primary consolidation](#settlement_field)
- [Vertical elastic-strain integration through layers](#settlement_elastic)
- [Square-footing settlement with the fixed influence diagram](#schmertmann)

<a id="bearing"></a>

## Undrained footing resistance with biaxial eccentricity

**Worksheet:** Undrained bearing capacity.

### Formulation

```math
\begin{gathered}
B'=B-2\frac{|M_y|}{N},\quad L'=L-2\frac{|M_x|}{N},\quad q_d=\frac{N}{B'L'}\\
q_{u,net}=N_c s_u,\qquad q_{a,gross}=\frac{N_c s_u}{F_s}+\gamma D\\
p(x,y)=\max(0,a+b_xx+b_yy),\quad \int_A p\,dA=N,\quad
\int_A xp\,dA=M_y,\quad \int_A yp\,dA=M_x
\end{gathered}
```

B and L are the base dimensions; N is the total vertical resultant; Mx and My act about the stated axes. su is undrained strength, Nc the selected geometry factor, D embedment and Fs the net-resistance safety factor. The effective area is a resistance idealization. The full-contact trial uses 6|My|/(NB)+6|Mx|/(NL) ≤ 1 as the biaxial kern condition. Outside it, the worksheet fits the pressure plane coefficients to the three equilibrium equations on the rectangular base and reports the positive pressure zone separately.

### Inputs and units

| Input |
| --- |
| Width B (m) |
| Length L (m) |
| Embedment D (m) |
| Overburden unit weight (kN/m3) |
| Undrained strength (kPa) |
| Selected Nc |
| Vertical load N (kN) |
| Moment about X (kN m) |
| Moment about Y (kN m) |
| Net capacity safety factor |
| Undrained interface adhesion (kPa; optional) |
| Sliding resistance factor (optional) |

**Optional actions table:** Action and source reference; Vertical force (+ down, kN); Horizontal force X (kN); Horizontal force Y (kN); Application X (m); Application Y (m); Application Z above base (m); Applied moment (+ loads +Y, kN m); Applied moment (+ loads +X, kN m).

Enter one already assembled load combination per saved case. With this table, leave the direct N, Mx and My fields blank. Enter weights as positive vertical forces and uplift as negative. Use the centre of the footing base as the origin. The table adds the following lever terms to the supplied couples:

```math
M_x=\sum_i (M_{x,i}+y_i N_i+z_i H_{y,i}),\qquad M_y=\sum_i(M_{y,i}+x_i N_i+z_i H_{x,i})
```

The reported X and Y moments use the pressure signs in the input labels. Torsion from horizontal force offsets is reported as Σ(xHy−yHx). Blank force and couple components are zero. Enter the applicable lever coordinates explicitly, including zero at the origin. Keep the input and base schedules together when reviewing the combination.

### Outputs and application

Results include Effective width (m); Effective length (m); Effective area (m2); Gross demand (kPa); Net ultimate resistance (kPa); Gross ultimate resistance (kPa); Gross allowable pressure (kPa); Demand / allowable; Biaxial kern utilization; Full-contact trial minimum (kPa); Full-contact trial maximum (kPa).

For partial contact, the worksheet also reports the compression-only area, peak pressure, pressure at the outline vertices and equilibrium residuals. The plan distinguishes the contact outline from the effective area.

The action table reports the reduced base forces and moments by source row. With the action table and both interface inputs, the worksheet compares inclined bearing and sliding using the same base resultant. With both interface inputs blank, horizontal force or torsion suppresses the vertical bearing utilization. The worksheet adds no automatic loads or partial factors.

For a horizontal base on homogeneous soil in undrained conditions, let H be the magnitude of the horizontal resultant, Aeff the effective area, Ac the calculated compression area, and a the adopted interface adhesion between zero and su. The sliding factor Fsl must be at least 1.

```math
\begin{gathered}
A_{eff}=B'L',\qquad i_c=\frac{1+\sqrt{1-H/(s_uA_{eff})}}{2}\\
q_{a,incl}=\gamma D+\frac{N_c s_u i_c}{F_s},\qquad
R_{sl}=\frac{a\min(A_{eff},A_c)}{F_{sl}}
\end{gathered}
```

The inclination factor follows DB SE-C Annex F, equation F.6, using effective dimensions. It is applied for all H within the equation's domain, including small horizontal loads. The sliding worksheet conservatively limits the adhesion area to the smaller of the two areas and takes no credit for passive resistance. It reports the signed reserve Rsl − H, including when the adopted resistance is zero. Torsion suppresses both comparisons. If H exceeds su × Aeff, the inclination equation is outside its domain and only the sliding comparison is reported. Select the actions and factors on a consistent design basis.

**Application conditions:** B,L,N,su,Nc >0; D,gamma >=0; FS >=1. Effective dimensions B-2|My|/N and L-2|Mx|/N must remain positive. The contact model assumes a rigid base and a linear response in compression. Contact loss must be reviewed for the load combination.

**References:** [gec6](BIBLIOGRAPHY.md#gec6), [biaxial contact](BIBLIOGRAPHY.md#biaxial_contact), [DB SE-C Cimientos, §4.3.1.1 and Annex F](https://www.codigotecnico.org/pdf/Documentos/SE/DBSE-C.pdf).


<a id="bearing_drained"></a>

## General-shear footing resistance using effective stresses

**Worksheet:** Drained bearing - Vesic factors / FHWA shape.

### Formulation

```math
\begin{gathered}
q_u=c'N_c s_c+q'N_q s_q+\frac12\gamma' B_{\mathrm{eff}} N_\gamma s_\gamma\\
N_q=e^{\pi\tan\phi'}\tan^2\left(45^\circ+\frac{\phi'}2\right),\quad N_c=\frac{N_q-1}{\tan\phi'},\quad N_\gamma=2(N_q+1)\tan\phi'
\end{gathered}
```

c′ and φ′ are effective strength parameters; q′ is effective overburden at the base and γ′ the adopted effective unit weight below it. For original B≤L and L/B<5, sc=1+(B/L)Nq/Nc, sq=1+(B/L)tanφ′ and sγ=1−0.4B/L. At φ′=0 use Nc=π+2, Nq=1, Nγ=0, sc=1+B/(5L), sq=sγ=1. Strip factors equal one for L/B≥5. Original dimensions determine shape factors, following FHWA section 5.2.4.

Base moments give eB=|M_B/V| and eL=|M_L/V|, B′=B−2eB, L′=L−2eL and A′=B′L′ (FHWA equations 6-6/6-7). The weight term uses the smaller of B′ and L′; applied bearing pressure is V/A′. This effective area is not the actual compression-only contact area. Blank moments mean zero. Include horizontal-load lever arms in the supplied base moments.

Choose **Supplied effective stresses** to enter q′ and γ′ directly, or **FHWA water factors (Table 5-3)** to supply uniform soil unit weight, base depth Df and water depth Dw below ground. Blank Dw means dry. The latter interpolates CWq from 0.5 at ground to 1 at the base, and CWγ from 0.5 at/below the base to 1 at Df+1.5Beff. Then q′=γDfCWq and γ′=γCWγ. These are the table's simplified half-weight approximations, not an exact hydrostatic integration with measured saturated weights. The two approaches are alternatives; water corrections are applied once.

The worksheet distinguishes qu/Fs from q′+(qu−q′)/Fs; select the convention appropriate to the project. For horizontal resultant H>0, enter interface friction δ and the required sliding safety factor. Frictional sliding uses FR=Vtanδ and FSsliding=FR/H (FHWA equations 5-38/5-40), without adhesion or passive resistance. V must be the justified simultaneous effective stabilizing load after uplift. Separate bearing and sliding follow section 5.2.3.7; no additional load-inclination factor is multiplied into the shape-corrected bearing resistance. Unusual loading configurations require separate assessment.

### Inputs and units

| Input |
| --- |
| Width B (m; B <= L) |
| Length L (m) |
| Effective cohesion (kPa) |
| Effective friction angle (deg; 0-45) |
| Effective surcharge at base q (kPa) |
| Effective unit weight below base (kN/m3) |
| Comparison safety factor (>=1) |
| Gross effective vertical resultant V (kN) |
| Base moment causing eccentricity across B (kN m; blank = 0) |
| Base moment causing eccentricity across L (kN m; blank = 0) |
| Water treatment |
| Base depth Df below ground (m; water-factor method) |
| Uniform soil unit weight (kN/m3; water-factor method) |
| Water depth Dw below ground (m; blank = dry) |
| Horizontal resultant H at base (kN; blank = 0) |
| Drained base friction angle delta (deg; sliding) |
| Required sliding safety factor (>=1) |

### Outputs and application

Results include Nc; Nq; Ngamma; sc; sq; sgamma; Cohesion contribution (kPa); Surcharge contribution (kPa); Weight contribution (kPa); Gross ultimate pressure (kPa); Net ultimate pressure (kPa); Net allowable pressure (kPa); Gross-basis allowable pressure (kPa); Net-basis allowable gross pressure (kPa); Applied gross effective pressure (kPa).

The Geometry tab and PDF show the footing plan, load-resultant location, effective bearing area and selected water scenario. Results also include effective dimensions, the water factors when selected, and frictional sliding when H>0.

**Application conditions:** 0 <= phi <= 45 deg; 0 < B <= L; c,q >=0; gamma,V >0; FS >=1. The resultant must lie inside the footing in both directions. H>0 requires phi>0 and 0<=δ<=phi. Homogeneous general shear, level ground/base; no depth-resistance credit, settlement, slope, compressibility, torsion or layered-ground verification. Outside the full-contact kern, review contact and rotation independently.

**References:** [gec6](BIBLIOGRAPHY.md#gec6).


<a id="footing_contact"></a>

## Uniaxial compression-only footing contact

**Worksheet:** Footing contact - uniaxial compression only.

### Formulation

```math
\begin{gathered}
e=\frac MN,\qquad q_{max,min}=\frac{N}{BL}\left(1\mathbin{\pm}\frac{6|e|}{B}\right)\quad(|e|\leq B/6)\\
a=3\left(\frac B2-|e|\right),\qquad q_{max}=\frac{2N}{La}\quad(B/6\lt |e|\lt B/2)
\end{gathered}
```

M is the signed moment causing pressure variation across B, and N the positive vertical resultant. L is the uniform transverse base length. Full contact is linear; partial contact is a triangular compression zone of width a. The diagram and integrated force/moment residuals support equilibrium review. A resultant at or outside the base edge does not admit the assumed finite compression-only distribution. Contact area and effective bearing-resistance area are different concepts.

### Inputs and units

| Input |
| --- |
| Width along pressure gradient B (m) |
| Length parallel to moment axis L (m) |
| Resultant compression N at base (kN) |
| Signed moment at base M (kN m) |

### Outputs and application

Results include Eccentricity M/N (m); Contact width (m); Contact area (m2); Minimum pressure (kPa); Maximum pressure (kPa); Force residual (kN); Moment residual (kN m).

**Application conditions:** B,L,N >0; signed M with |M/N|<B/2. Uniaxial linear compression-only reaction, full or partial contact. No biaxial moment, resistance, settlement, code combinations or universal allowable pressure.

**References:** [gec6](BIBLIOGRAPHY.md#gec6).


<a id="foundation_service"></a>

## Compare supplied pressures and observed or supplied settlements

**Worksheet:** Foundation alternatives - supplied pressures and settlements.

### Formulation

```math
Q=qBL,\qquad k_s=\frac{q}{s/1000}
```

B and L are foundation dimensions in metres, q supplied pressure in kPa and s supplied settlement in mm. Q is the corresponding load in kN; ks is a secant coefficient in kN/m³ for that foundation and load state. The worksheet compares alternatives and a stated project settlement criterion. Pressure and settlement are inputs to this comparison, not predictions from this worksheet; ks is not an intrinsic soil constant.

### Inputs and units

| Input |
| --- |
| Project settlement limit (mm) |

**Cases table:** Width B (m); Length L (m); Embedment below excavation (m); Supplied pressure (kPa); Supplied settlement (mm); Reported load (kN; optional).


### Outputs and application

Results include Alternatives; Maximum supplied settlement / limit.

**Application conditions:** B,L,q,s and settlement limit >0; Df >=0; reported load >=0 if supplied. q and s are supplied data, not predicted resistance or settlement. No universal acceptable ks range.

**References:** [gec6](BIBLIOGRAPHY.md#gec6).


<a id="settlement"></a>

## Stress increments and one-dimensional primary consolidation

**Worksheet:** Stress and consolidation.

### Formulation

```math
\begin{gathered}
\Delta\sigma_z=\frac{3Qz^3}{2\pi(r^2+z^2)^{5/2}},\qquad r^2=(x-x_Q)^2+(y-y_Q)^2\\
s=\frac{H}{1+e_0}\left[C_r\log_{10}\frac{\sigma'_p}{\sigma'_0}+C_c\log_{10}\frac{\sigma'_f}{\sigma'_p}\right]\quad(\sigma'_f>\sigma'_p)
\end{gathered}
```

The first equation is the Boussinesq point-load kernel. Finite line and rectangular loads are integrated from this kernel; the separately selected centred 2:1 rectangle uses Δσz=qBL/[(B+z)(L+z)]. For each compressible sublayer, H is thickness, e0 initial void ratio, σ′0 initial effective stress and σ′f=σ′0+Δσz. Cc and Cr are the base-10 compression and recompression indices. If σ′f≤σ′p, use s=H Cr log10(σ′f/σ′0)/(1+e0). The entered preconsolidation stress σ′p must be at least σ′0. Layer contributions are evaluated at sublayer midpoints and summed; negative increments may produce rebound.

### Inputs and units

| Input |
| --- |
| Evaluation X (m) |
| Evaluation Y (m) |

**Loads table:** point / line / rectangle / rectangle_2to1; Q (kN), w (kN/m), q (kPa); X1 (m); Y1 (m); X2 (m); Y2 (m).


**Layers table:** Top (m); Bottom (m); Initial effective stress (kPa); Void ratio; Cc; Cr; Preconsolidation stress (kPa).


### Outputs and application

Results include Primary settlement (mm).

**Application conditions:** Layer thickness >0; initial and final effective stress >0; e0,Cc,Cr >=0; pc >= initial stress. Rectangular bounds increase; line length >0. Signed load increments permit unloading; 1D primary consolidation only.

**References:** [settlement](BIBLIOGRAPHY.md#settlement).


<a id="settlement_field"></a>

## Plan and section views of primary consolidation

**Worksheet:** Settlement field - Boussinesq / 1D primary consolidation.

### Formulation

```math
s(x,y)=\sum_j\frac{H_j}{1+e_{0,j}}\,\varepsilon_{\log,j}\bigl(\sigma'_{0,j},\Delta\sigma_z(x,y,z_j),\sigma'_{p,j}\bigr)
```

εlog denotes the Cr/Cc logarithmic expression documented under Stress and consolidation, before division by (1+e0). At each plan-grid point, the method superposes Boussinesq point, finite-line or rectangular load increments and evaluates the same primary-consolidation sublayers. Layer geometry and properties are laterally uniform. Reported extrema belong to the sampled grid; refine both sublayers and grid for the intended interpretation. A plotted settlement field represents independent flexible-load columns, not rigid-foundation compatibility.

### Inputs and units

| Input |
| --- |
| Map minimum X (m) |
| Map maximum X (m) |
| Map minimum Y (m) |
| Map maximum Y (m) |
| Grid points per axis (odd integer 3-31) |

**Loads table:** point / line / rectangle / rectangle_2to1; Q (kN), w (kN/m), q (kPa); X1 (m); Y1 (m); X2 (m); Y2 (m).


**Layers table:** Top (m); Bottom (m); Initial effective stress (kPa); Void ratio; Cc; Cr; Preconsolidation stress (kPa).


### Outputs and application

Results include Maximum sampled settlement (mm); Minimum sampled settlement / rebound (mm); Grid sample count.

**Application conditions:** Increasing X/Y bounds; odd grid size 3..31. 1..20 loads, 1..100 non-overlapping compressible sublayers. Positive initial/final effective stresses; pc >= initial, e0/Cc/Cr >=0. Boussinesq point/line/rectangle only; 2:1 excluded. Flexible loads, long-term primary consolidation, no rigid compatibility or time evolution.

**References:** [settlement](BIBLIOGRAPHY.md#settlement).


<a id="settlement_elastic"></a>

## Vertical elastic-strain integration through layers

**Worksheet:** Immediate settlement - elastic layered field.

### Formulation

```math
s(x,y)=\sum_j\frac{1}{M_j}\int_{z_{j,top}}^{z_{j,bottom}}\Delta\sigma_z(x,y,z)\,dz
```

Mj is the positive constrained modulus of a layer in kPa, not Young modulus E. Rectangular signed pressure increments act on a common surface; their Boussinesq stresses are superposed. Four-point Gauss integration is split at layer and integration-sublayer boundaries. The bottom displacement is prescribed zero. Output includes settlement maps, a selected vertical profile and layer contributions. Choose stress increments and moduli consistently with the loading scenario.

### Inputs and units

| Input |
| --- |
| Map X minimum (m) |
| Map X maximum (m) |
| Map Y minimum (m) |
| Map Y maximum (m) |
| Points per axis (odd, 3-21) |
| Maximum integration sublayer (m) |
| Profile X (m) |
| Profile Y (m) |

**Loads table:** Signed pressure INCREMENT (kPa); X1 (m); Y1 (m); X2 (m); Y2 (m).


**Layers table:** Top below load plane (m); Bottom (m); Constrained modulus M (kPa).


### Outputs and application

Results include Selected profile settlement (mm); Maximum sampled settlement (mm); Minimum sampled settlement / rebound (mm); Integration sublayers; Fixed bottom depth (m).

Save settlement as a separate service load case and include the combination identifier in its name. Enter the pressure change relative to the chosen initial condition over the loaded footprint. For a centred 360 kN service load on a 2 m by 2 m square with 20 kPa of excavation relief over the same area, the uniform pressure increment is 70 kPa. Use the actual loading geometry and increments for each case. Review the settlement and differential movement against the project criteria.

**Application conditions:** Flexible rectangular loads, 1-10; contiguous layers from z=0, 1-40; M>0, step>0; <=400 vertical sublayers. Odd map grid 3-21, <=2 million stress evaluations. Fixed bottom and linear vertical strain; no rigid-contact, plasticity or automatic excavation/water stages.

**References:** [settlement](BIBLIOGRAPHY.md#settlement), [elastic_columns](BIBLIOGRAPHY.md#elastic_columns), [preliminary sand stiffness](BIBLIOGRAPHY.md#sand_stiffness).


<a id="schmertmann"></a>

## Square-footing settlement with the fixed influence diagram

**Worksheet:** Schmertmann - square footing.

### Formulation

```math
\begin{gathered}
s=C_1C_2q_{net}\int_0^{2B}\frac{I_z(z)}{E_s(z)}\,dz,\qquad q_{net}=\frac{Q}{B^2}-\sigma'_{v0}\\
I_z=\max\left[0,\min\left(0.1+\frac zB,\;0.8-0.4\frac zB\right)\right]\\
C_1=\max\left(0.5,1-\frac{0.5\sigma'_{v0}}{q_{net}}\right),\quad C_2=1+0.2\log_{10}(t/0.1)
\end{gathered}
```

Q is service load, B square footing width, σ′v0 initial effective stress at the base, Es layer stiffness and t elapsed years. The immediate option uses C2=1; elapsed-time entries start at 0.1 year. The adopted diagram peaks at Iz=0.6 at z=0.5B and reaches zero at 2B. Integrals are split exactly at the peak. Supply positive Es through 2B, directly or through an explicitly justified Es/N ratio. This fixed-diagram variant is distinguished from the modified stress-dependent-peak formulation.

### Inputs and units

| Input |
| --- |
| Square footing width B (m) |
| Total service load (kN) |
| Initial effective stress at base (kPa) |
| Elapsed time (years; 0=immediate) |
| Selected Es/N ratio (kPa; optional) |

**Layers table:** Top below base (m); Bottom below base (m); Direct Es (kPa); SPT N (if using Es/N).


### Outputs and application

Results include Gross pressure (kPa); Net pressure (kPa); Embedment factor C1; Time factor C2; Influence depth (m); Settlement (mm).

**Application conditions:** Square footing B >0; net pressure >0; initial effective stress >=0. Time 0 or >=0.1 years. Contiguous layers cover 0..2B below base; Es >0 OR N >0 with justified Es/N >0. No automatic Es/N correlation.

**References:** [schmertmann](BIBLIOGRAPHY.md#schmertmann), [preliminary sand stiffness](BIBLIOGRAPHY.md#sand_stiffness).
