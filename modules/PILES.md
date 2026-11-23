# Deep foundations

[Module index](../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Axial resistance of piles using the lambda method](#pile)
- [Axial pile resistance with directly selected K and Nq](#pile_sand)
- [Axial sand-pile resistance with bounded chart factors](#pile_coyle)
- [Compare diameter and embedded-length alternatives](#pile_design)
- [Compare supplied pile capacities and convert force units](#pile_comparison)
- [Converse–Labarre group efficiency](#pile_group)
- [Axial load–displacement response with supplied t-z and q-z laws](#pile_transfer)
- [Sand-derived resistance limits coupled to axial load transfer](#pile_soil_transfer)
- [Axial cyclic resistance envelope](#pile_cyclic)
- [Rigid pile cap load distribution](#pile_cap)
- [Negative skin friction](#pile_downdrag)
- [Individual pile settlement](#pile_settlement_rom)
- [Ultimate lateral soil resistance](#pile_lateral_ultimate)
- [Nonlinear lateral pile response](#pile_lateral_py)

<a id="pile_lateral_py"></a>

## Nonlinear lateral pile response

**Worksheet:** Pile lateral response - nonlinear hyperbolic p-y.

An elastic Euler-Bernoulli pile is supported by nonlinear soil springs. The
monotonic hyperbolic relation follows Stuedlein and Li (2018), section
2.5.11, p. 47, equation 2.92, expressed symmetrically for either load direction:

```math
p(y)=\frac{p_{ult}y}{y_{50}+|y|},\qquad K_0=\frac{p_{ult}}{y_{50}},\qquad R_i=h_i p(y_i)
```

Here p is force per unit pile length (kN/m), y and y50 are in metres in the
equation, and hi is the spring tributary length (m). Input y50 is in **mm** and
is converted once. Supply pult and y50 justified for the actual pile geometry,
soil, depth and loading condition. Do not multiply line resistance by pile width
again. The parameters are constant within each layer; subdivide layers to
represent depth variation. This hyperbola is not a universal sand/clay curve.

### Inputs and units

| Input |
| --- |
| Embedded pile length (m) |
| Pile material elastic modulus E (MPa) |
| Bending inertia I (m4) |
| Ground-level horizontal force H (kN; signed) |
| Ground-level head moment M (kN m; signed) |
| Head rotation condition |
| Upper unsupported depth (m) |
| Maximum spring tributary length (m) |
| Project head displacement limit (mm) |

**Layers table:** Top (m); Bottom (m); Ultimate line reaction pult (kN/m);
Displacement at half pult, y50 (mm).

Free rotation or restrained rotation may be selected at the head; translation
remains free. Layers cover zero to toe; zero pult disables that layer's reaction.

### Outputs and application

Profiles show displacement, rotation, shear, bending moment and soil reaction.
For a restrained head, the additional restraint moment is reported separately
from the entered action. The toe is free. Positive head force and moment
reinforce head displacement with free rotation. Depth is positive downwards;
positive rotation follows the beam coordinate from toe to head. The schedule
reports shear and bending on the headward element side of each spring node;
shear jumps across the concentrated spring reaction.

The model uses constant elastic EI, small displacements and a monotonic,
symmetric p-y law. It does not model cyclic memory, plastic section resistance,
P-delta effects or group interaction. Groundwater and other site effects must
already be reflected in the justified soil curves. Check mesh sensitivity and
structural resistance separately; the user displacement limit is a project
criterion, not an automatic code verification. A failed equilibrium produces
an error rather than a partial calculation report.

**References:** [Hyperbolic lateral pile response](BIBLIOGRAPHY.md#pile_hyperbolic).

<a id="pile_cyclic"></a>

## Axial cyclic resistance envelope

**Worksheet:** Pile cyclic axial loading - ROM 0.5-05.

### Formulation

The method follows ROM 0.5-05, section 3.6.3.5, Figure 3.6.6 (printed
pp. 238-241). Compression is positive. Actions act at ground level and exclude
the embedded pile weight, which is accounted for separately. Static resistance
components are **unfactored**.

```math
Q_h=R_f+R_p-W',\qquad T_a=\tfrac12 R_f+W'
```

```math
\alpha=R_p/R_f,\qquad \beta=W'/T_a,\qquad
\eta=\max\{\tfrac12+\alpha-\beta(1+\alpha),\;1-\beta\}
```

```math
Q=(Q_{max}+Q_{min})/2,\qquad \Delta Q=(Q_{max}-Q_{min})/2
```

The diagram is bounded by `Q + ΔQ ≤ Qh`, `ΔQ − Q ≤ Ta` and
`ΔQ ≤ η Ta`. The safety factor is the radial load multiplier `F = OB / OA`
of Figure 3.6.6. Intersecting that ray with the three boundaries gives:

```math
F=\min\left\{\frac{Q_h}{Q_{max}},\;
\frac{T_a}{-Q_{min}},\;\frac{\eta T_a}{\Delta Q}\right\}
```

Include the compression term only when `Qmax > 0`, the uplift term only when
`Qmin < 0`, and the cyclic term only when `ΔQ > 0`. Thus equal nonzero extremes
recover a static check. A zero/zero case has no load multiplier and is rejected.
`F ≥ Frequired` meets the adopted radial-factor criterion. The diagram also
shows the envelope divided by the required factor and the entered load points.

### Inputs and units

| Input | Definition |
| --- | --- |
| Static compression shaft resistance Rf (kN; unfactored) | Positive static shaft resistance in compression, before safety factors |
| Static toe resistance Rp (kN; unfactored) | Nonnegative static toe resistance, before safety factors |
| Effective embedded pile weight W' (kN) | Nonnegative effective embedded weight, including buoyancy |
| Required radial safety factor F | Project-adopted minimum, at least 1 |
| Minimum axial head load (kN; compression positive) | Lower signed axial extreme |
| Maximum axial head load (kN; compression positive) | Upper signed axial extreme on the same action basis, not below the minimum |

### Worked example

For `Rf = 1000 kN`, `Rp = 500 kN` and `W' = 100 kN`,
`Qh = 1400 kN`, `Ta = 600 kN` and `η Ta = 500 kN`.
Load extremes of `100 kN` and `500 kN` give `Q = 300 kN` and
`ΔQ = 200 kN`. The compression multiplier is `2.8`; the cyclic multiplier
is `2.5`. Uplift is inactive, so the radial factor is `2.5`.

### Outputs and application

Results include nominal head resistances, alpha, beta, eta, mean load,
amplitude, component multipliers, radial factor and required/calculated factor.
The uplift expression follows section 3.6.7.1; the compression head equilibrium
follows section 3.6.4.1. All three constraints govern the plotted envelope.

This is a stationary **axial** envelope for many cycles on an individual vertical
pile. It does not calculate cycle-count accumulation, fatigue life, accumulated
displacement, lateral p-y hysteresis, liquefaction, group effects or structural
resistance. No few-cycle relief or loading-rate strength increase is assumed.
For photovoltaic work, establish applicability, action combinations and the
required factor for the project. It is not an automatic Eurocode verification.

**References:** [ROM 0.5-05](BIBLIOGRAPHY.md#pile_cyclic).

<a id="pile"></a>

## Axial resistance of piles using the lambda method

**Worksheet:** Pile axial capacity - lambda.

### Formulation

```math
\begin{gathered}
Q_s=\pi D\lambda\int_0^L(\sigma'_v+2s_u)\,dz,\qquad Q_b=\frac{\pi D^2}{4}N_{c,b}s_{u,b}\\
Q_a=\frac{Q_s}{F_{s,s}}+\frac{Q_b}{F_{s,b}}
\end{gathered}
```

D is diameter, L embedded length and λ the adopted empirical coefficient. σ′v comes from the entered total unit weights minus hydrostatic pore pressure; su is the shaft-layer undrained strength. Nc,b and su,b are the selected toe factor and representative below-toe strength. The shaft integral is piecewise exact for the entered constant layer properties. Select λ for the pile construction and ground conditions; the toe strength is not silently taken from the final shaft row.

### Inputs and units

| Input |
| --- |
| Pile diameter (m) |
| Pile length (m) |
| Selected lambda |
| Water table depth (m; blank = dry) |
| Water unit weight (kN/m3) |
| Representative below-toe strength (kPa) |
| Selected toe Nc |
| Shaft safety factor |
| Toe safety factor |

**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Undrained strength (kPa).


### Outputs and application

Results include Ultimate shaft resistance (kN); Ultimate toe resistance (kN); Ultimate axial resistance (kN); Allowable axial load (kN).

**Application conditions:** D,L >0; layers cover embedded length; gamma >0, su >=0; 0 < lambda <=1; toe su,Nc >0; selected factors require method-specific justification; FS >=1. Water depth >=0 or blank=dry. Lambda is not a drained sand or rock-socket model.

**References:** [lambda](BIBLIOGRAPHY.md#lambda), [gec10](BIBLIOGRAPHY.md#gec10).


<a id="pile_sand"></a>

## Axial pile resistance with directly selected K and Nq

**Worksheet:** Sand - K tan(delta), direct Nq.

### Formulation

```math
\delta=r_\delta\phi',\quad\beta=K\tan\delta,\quad Q_s=\pi D\int_0^L\beta\sigma'_{v,lim}\,dz,\quad Q_b=\frac{\pi D^2}{4}\sigma'_{v,b}N_q
```

rδ is the entered interface/soil friction-angle ratio. K and Nq are supplied coefficients. Layers mode integrates constant material properties and splits water and stress-cap boundaries. Nodes mode integrates nodal unit shaft friction by trapezoids; add nodes at property changes. An optional limiting depth affects shaft stress only. Separate shaft and toe factors produce allowable compression. Optional uplift uses reduced shaft resistance plus effective pile weight; a supplied uplift ratio is not automatically inferred from compression capacity.

### Inputs and units

| Input |
| --- |
| Pile diameter (m) |
| Pile length (m) |
| Interface delta / soil phi |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Shaft limiting depth (m; blank=none) |
| Shaft safety factor |
| Toe safety factor |
| Uplift: pile unit weight (kN/m3) |
| Uplift: shaft resistance ratio |
| Uplift: shaft safety factor |
| Selected toe Nq |

**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Friction angle (degrees); Selected K.


**Nodes table:** Depth (m); Unit weight to next node (kN/m3); Friction angle (degrees); Selected K.


### Outputs and application

Results include Embedded L/D; Pile perimeter (m); Toe area (m2); Toe Nq; Ultimate shaft resistance (kN); Ultimate toe resistance (kN); Ultimate compression resistance (kN); Allowable soil resistance (kN); Allowable soil resistance (tf); Effective pile self-weight (kN); Allowable uplift at head (kN).

**Application conditions:** D,L > 0; profile covers 0..L with contiguous layers OR increasing nodes. 0 <= phi < 60 deg; delta/phi and uplift ratio 0..1; FS >= 1. Water depth >=0 or blank=dry; effective stresses cannot be negative. Direct K,Nq >=0 must be justified; numerical acceptance is not correlation validity.

**References:** [gec10](BIBLIOGRAPHY.md#gec10), [coyle](BIBLIOGRAPHY.md#coyle).


<a id="pile_coyle"></a>

## Axial sand-pile resistance with bounded chart factors

**Worksheet:** Sand - Coyle-Castello chart tables.

### Formulation

```math
\log_{10}F=(1-a)\bigl[(1-b)\log_{10}F_{00}+b\log_{10}F_{01}\bigr]+a\bigl[(1-b)\log_{10}F_{10}+b\log_{10}F_{11}\bigr]
```

F denotes K or Nq; a and b are the fractional coordinates within a bounding L/D and friction-angle cell. The application evaluates a bounded numerical chart approximation, then uses the same β-method integration as the direct-factor sand-pile worksheet. K covers φ=30–36° and L/D=0–35; Nq covers φ=30–40° and L/D=0–70. Both domains must hold in a combined calculation. Interpolation is logarithmic and extrapolation is rejected. The empirical Coyle–Castello correlations concern piles driven in sand; justify transfer to a different construction method. The numerical approximation is not presented as an exact transcription of a published graphical curve.

### Inputs and units

| Input |
| --- |
| Pile diameter (m) |
| Pile length (m) |
| Interface delta / soil phi |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Shaft limiting depth (m; blank=none) |
| Shaft safety factor |
| Toe safety factor |
| Uplift: pile unit weight (kN/m3) |
| Uplift: shaft resistance ratio |
| Uplift: shaft safety factor |
| K chart shaft angle (degrees) |
| Representative toe phi (degrees) |

**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Friction angle (degrees).


**Nodes table:** Depth (m); Unit weight to next node (kN/m3); Friction angle (degrees).


### Outputs and application

Results include Embedded L/D; Pile perimeter (m); Toe area (m2); Toe Nq; Ultimate shaft resistance (kN); Ultimate toe resistance (kN); Ultimate compression resistance (kN); Allowable soil resistance (kN); Allowable soil resistance (tf); Effective pile self-weight (kN); Allowable uplift at head (kN).

**Application conditions:** D,L > 0; profile covers 0..L with contiguous layers OR increasing nodes. 0 <= phi < 60 deg; delta/phi and uplift ratio 0..1; FS >= 1. Water depth >=0 or blank=dry; effective stresses cannot be negative. Coyle K: phi 30..36 deg, L/D 0..35; Nq: phi 30..40 deg, L/D 0..70. No extrapolation. Combined shaft/toe use is limited by BOTH domains.

**References:** [coyle](BIBLIOGRAPHY.md#coyle).


<a id="pile_design"></a>

## Compare diameter and embedded-length alternatives

**Worksheet:** Sand - diameter / length design table.

### Formulation

```math
Q_a(D,L)=\frac{Q_s(D,L)}{F_{s,s}}+\frac{Q_b(D,L)}{F_{s,b}}
```

Each D/L row is recalculated with its own geometry and bounded K/Nq chart factors on the common ground profile. Shaft and toe resistance, compression and optional uplift are tabulated for comparison. Alternative safety factors are explicit comparison choices. Every alternative must satisfy the factor-domain and profile-coverage conditions. The table supports engineering selection; it is not an automatic structural or cost optimization.

Optional nonnegative head compression and uplift demands add margins equal to
the calculated allowable head resistance minus the corresponding supplied demand
(kN). Demand and resistance must use the same allowable-load basis. Uplift demand
requires the pile unit weight, shaft resistance ratio and uplift safety factor.
The summary identifies the shortest passing **entered** circular-pile candidate
for all supplied axial demands; no intermediate length is calculated. Lateral,
cyclic, downdrag, settlement and structural checks remain separate. This
allowable-resistance comparison is not a Eurocode partial-factor verification.

### Inputs and units

| Input |
| --- |
| Interface delta / soil phi |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Shaft limiting depth (m; blank=none) |
| Shaft safety factor |
| Toe safety factor |
| Uplift: pile unit weight (kN/m3) |
| Uplift: shaft resistance ratio |
| Uplift: shaft safety factor |
| Alternate shaft FS (optional) |
| Alternate toe FS (optional) |

Optional demand inputs: **Allowable-basis head compression demand (kN; optional)** and
**Allowable-basis head uplift demand (kN; optional)**. Leave either blank to omit that
comparison.

**Cases table:** Diameter (m); Length (m); K chart shaft angle (degrees); Toe angle (degrees).


**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Friction angle (degrees).


**Nodes table:** Depth (m); Unit weight to next node (kN/m3); Friction angle (degrees).


### Outputs and application

Results include Number of capacity rows.

**Application conditions:** D,L > 0; profile covers 0..L with contiguous layers OR increasing nodes. 0 <= phi < 60 deg; delta/phi and uplift ratio 0..1; FS >= 1. Water depth >=0 or blank=dry; effective stresses cannot be negative. Coyle K: phi 30..36 deg, L/D 0..35; Nq: phi 30..40 deg, L/D 0..70. No extrapolation. Combined shaft/toe use is limited by BOTH domains. Every diameter/length alternative must be within the chart domains.

**References:** [coyle](BIBLIOGRAPHY.md#coyle), [gec10](BIBLIOGRAPHY.md#gec10).


<a id="pile_comparison"></a>

## Compare supplied pile capacities and convert force units

**Worksheet:** Capacity table and unit conversion.

### Formulation

```math
Q_a=Q_s/F_{s,s}+Q_b/F_{s,b},\qquad Q_{tf}=Q_{kN}/9.80665
```

Enter shaft and toe capacities for each diameter/length pair and identify their basis as ultimate or already allowable. Already allowable values use factors of one and are not reduced a second time. The exact standard-gravity conversion is 1 metric tonne-force=9.80665 kN. This worksheet compares supplied values; their geotechnical derivation remains with their source.

### Inputs and units

| Input |
| --- |
| Capacity basis (0=ultimate; 1=already allowable; blank=0) |
| Shaft safety factor |
| Toe safety factor |
| Alternate shaft FS (optional) |
| Alternate toe FS (optional) |

**Cases table:** Diameter (m); Length (m); Supplied shaft (kN; selected basis); Supplied toe (kN; selected basis).


### Outputs and application

Results include Number of capacity rows.

**Application conditions:** D,L >0 and unique combinations; supplied shaft/toe >=0; FS >=1. Basis 0=ultimate, 1=already allowable. Already allowable requires FS=1 and no alternative factors; arithmetic comparison only.

**References:** [si_units](BIBLIOGRAPHY.md#si_units), [gec10](BIBLIOGRAPHY.md#gec10).


<a id="pile_group"></a>

## Converse–Labarre group efficiency

**Worksheet:** Pile group - Converse-Labarre screening.

### Formulation

```math
\eta=1-\frac{\theta\bigl[(n-1)m+(m-1)n\bigr]}{90mn},\quad\theta=\tan^{-1}(D/s)\ \text{in degrees},\quad Q_g=\eta mnQ_1
```

m and n are integer row/column counts, D pile diameter, s common centre spacing and Q1 the single-pile capacity on a stated ultimate or allowable basis. Qg retains that basis. The continuous expression is used throughout the admitted spacing range. Use the empirical relation for a regular group of identical piles and assess group settlement, block failure and load distribution under the project-specific design procedure.

### Inputs and units

| Input |
| --- |
| Number of columns |
| Number of rows |
| Pile diameter D (m) |
| Equal centre-to-centre spacing s (m) |
| Single pile resistance (kN; selected basis) |

### Outputs and application

Results include Pile count; Spacing / diameter; Angle theta (degrees); Group efficiency (%); Sum of individual resistances (kN); Efficiency-adjusted resistance (kN; same basis).

**Application conditions:** Rows/columns: integers 1..100; D and single-pile capacity >0; centre spacing >D. Converse-Labarre screening for an identical rectangular group; no block failure or group settlement verification.

**References:** [group](BIBLIOGRAPHY.md#group).


<a id="pile_transfer"></a>

## Axial load–displacement response with supplied t-z and q-z laws

**Worksheet:** Pile axial load-transfer - supplied t-z / q-z laws.

### Formulation

```math
t(w)=t_u\frac{w}{w_{50}+w},\qquad q(w_b)=q_u\frac{w_b}{w_{b,50}+w_b},\qquad K_{bar}=\frac{EA}{\ell}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}
```

tu and qu are positive limiting unit shaft and base resistances, w and wb local downward displacements, and w50/wb,50 their half-mobilization displacements. E is pile Young modulus, A area and ℓ element length. The elastic axial pile is assembled with independent nonlinear soil springs and iterated to head-load equilibrium. Enter displacement calibration in mm and E in MPa; internal assembly uses metres and kPa. Review load balance, convergence and mesh refinement. Applied compression must remain below the asymptotic shaft-plus-base limit.

### Inputs and units

| Input |
| --- |
| Shaft / toe diameter (m) |
| Pile elastic modulus (MPa) |
| Applied head compression increment (kN) |
| Maximum axial element length (m) |
| Ultimate unit tip resistance (kPa) |
| Tip displacement at 50% resistance (mm) |

**Layers table:** Layer top (m); Layer bottom (m); Ultimate unit shaft resistance (kPa); Shaft displacement at 50% resistance (mm).


### Outputs and application

Results include Head settlement (mm); Toe settlement (mm); Elastic pile shortening (mm); Mobilized shaft (kN); Mobilized toe (kN); Force balance residual (kN); Maximum nodal residual (kN); Asymptotic resistance, no FS (kN).

**Application conditions:** D,E,load,mesh step and half-mobilization displacements >0; shaft/toe limits >=0. 1..400 contiguous layers from zero, at most 400 elements. Applied compression < asymptotic shaft+toe capacity. Independent hyperbolic springs and constant elastic EA; no lateral, group, cyclic, uplift or structural failure analysis.

**References:** [gec10](BIBLIOGRAPHY.md#gec10).


<a id="pile_soil_transfer"></a>

## Sand-derived resistance limits coupled to axial load transfer

**Worksheet:** Sand axial response - beta / Nq and load transfer.

### Formulation

```math
t_u(z)=\beta(z)\sigma'_v(z),\qquad q_u=N_q\sigma'_{v,b}
```

Supply contiguous soil layers from pile head at ground level to toe, total unit weights, groundwater and selected β and Nq. The worksheet derives effective stresses and resistance limits, then solves the hyperbolic t-z/q-z model documented above. Half-mobilization displacements remain calibration inputs. Inspect derived limits and displacement/force profiles separately; load-transfer calibration and a resistance factor selection are different engineering decisions.

### Inputs and units

| Input |
| --- |
| Shaft / toe diameter (m) |
| Pile elastic modulus (MPa) |
| Applied head compression increment (kN) |
| Maximum axial element length (m) |
| Tip displacement at 50% resistance (mm) |
| Selected toe Nq |
| Water depth (m; blank=dry) |
| Water unit weight (kN/m3) |

**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Selected shaft beta; Shaft displacement at 50% resistance (mm).


### Outputs and application

Results include Head settlement (mm); Toe settlement (mm); Elastic pile shortening (mm); Mobilized shaft (kN); Mobilized toe (kN); Force balance residual (kN); Maximum nodal residual (kN); Asymptotic resistance, no FS (kN); Derived ultimate shaft (kN); Derived ultimate toe (kN).

**Application conditions:** Sand, user-selected beta and Nq >=0; 1..30 contiguous soil layers from ground/pile head to toe. Hydrostatic water, total gamma>0, effective stress>=0. At most 400 elements. Calibrated hyperbolic compression only; no group, downdrag, self-weight, lateral or structural checks.

**References:** [gec10](BIBLIOGRAPHY.md#gec10).


<a id="pile_cap"></a>

## Rigid pile cap - vertical spring load distribution

**Worksheet:** Rigid pile cap - vertical spring load distribution.

### Formulation

```math
N_i=k_i(w+a(x_i-x_c)+b(y_i-y_c)),\quad \sum N_i=N,\quad \sum y_iN_i=-M_x,\quad \sum x_iN_i=M_y
```

Coordinates and adopted axial group spring stiffnesses -> rigid plane compatibility -> vertical and two moment equilibria -> pile forces, settlements and optional resistance utilization.

### Inputs and units

| Input |
| --- |
| Cap vertical load N (kN; compression positive) |
| Applied right-hand moment Mx (kN m) |
| Applied right-hand moment My (kN m) |

**Piles table:** Pile X (m); Pile Y (m); Adopted axial spring stiffness (kN/m); Compression resistance (kN; optional, same load basis); Uplift resistance (kN; optional, same load basis).

### Outputs and application

Positive compression is the upward pile reaction supporting the cap; X/Y/upward Z are right-handed. Applied moments are right-handed: a downward force at positive Y has negative Mx. Enter group-adjusted AXIAL stiffness in kN/m. Moment modes unsupported by a single or collinear pile layout are rejected. Bilateral springs allow uplift; tension resistance and the pile-cap connection require review. Optional capacities must use the same load/factor basis. No lateral shear, torsion, cap bending or inclined piles is solved.

**Application conditions:** 1..200 distinct vertical piles; positive supplied axial stiffness (kN/m). Rigid cap with bilateral axial response. Applied moments must be equilibrated by the layout. Same action/resistance basis for optional checks; no lateral load, torsion, cap bending, inclined piles or automatic group interaction.

**References:** Puertos del Estado, ROM 0.5-05 (2005), section 3.6.10.1, printed p. 273. Rigid-cap compatibility and three-component equilibrium for supplied, group-adjusted axial springs; vertical piles only. [ROM bibliography](BIBLIOGRAPHY.md#rom_piles).


<a id="pile_downdrag"></a>

## Pile negative skin friction - adopted or compatible neutral depth

**Worksheet:** Pile negative skin friction - adopted or compatible neutral depth.

### Formulation

```math
R^-=C\int_0^{z_n}\tau^-(z)\,dz,\qquad Q_{below}=Q_{head}+W\prime+R^-
```

Adopted neutral depth or reviewed settlement compatibility -> integrate mobilized negative shaft stress over actual contact perimeter -> drag load and total transferred load below the drag zone.

### Inputs and units

| Input |
| --- |
| Embedded pile length (m) |
| Soil-contact perimeter (m) |
| Head compression load (kN) |
| Effective embedded pile weight (kN) |
| Adopted neutral depth (m; blank=use settlement curves) |

**Layers table:** Top (m); Bottom (m); Mobilized negative shaft stress (kPa).

**Settlements table:** Trial neutral depth (m); Free-field ground settlement at depth (mm); Pile settlement for this trial drag zone (mm).

### Outputs and application

C is actual contact perimeter. Supply an adopted neutral depth OR trial compatibility data. For each trial depth, pile settlement must come from a calculation including head load, weight, drag and the remaining supporting zone. It is not the movement-versus-depth profile of one load case. The code interpolates one monotonic crossing; coincident or ambiguous crossings are rejected. This does not generate a consolidation field or apply a pile-group drag limit. Check positive resistance below the drag zone and structural axial force separately.

**Application conditions:** Positive length/perimeter; nonnegative drag stresses, head compression and weight. Layers contiguous from zero to toe. Adopted neutral depth 0..L OR increasing trial depths covering 0..L with a unique decreasing settlement-difference crossing. Group and consolidation calculations are separate.

**References:** Puertos del Estado, ROM 0.5-05 (2005), section 3.6.3.4.1, pp. 232-234, Figure 3.6.3. Perimeter integration and neutral-depth compatibility of free-field and trial pile settlements. [ROM bibliography](BIBLIOGRAPHY.md#rom_piles).


<a id="pile_settlement_rom"></a>

## Pile settlement - ROM 0.5-05 simplified service model

**Worksheet:** Pile settlement - ROM 0.5-05 simplified service model.

### Formulation

```math
s=\left[\frac{D}{40Q_h}+\frac{l_1+\alpha l_2}{AE}\right]P,\qquad K_v=P/s
```

Nominal head resistance and pile geometry/material -> ROM soil flexibility plus elastic shortening -> service head settlement and equivalent secant axial spring stiffness.

### Inputs and units

| Input |
| --- |
| Equivalent pile diameter D (m) |
| Pile material area A (m2) |
| Pile elastic modulus E (MPa) |
| Free pile length l1 (m) |
| Embedded pile length l2 (m) |
| Load-transfer factor alpha (0.5..1) |
| Nominal static head compression resistance Qh (kN) |
| Service head compression P (kN) |
| Project settlement limit (mm) |

### Outputs and application

Use metres, kN, material area in m2 and E in MPa (converted to kN/m2). Equivalent diameter and material area are separate for justified noncircular profiles. Alpha ranges from 0.5 (floating) to 1 (predominantly end bearing). Qh is nominal head failure resistance, not an allowable load. Kv is the finite flexibility inverse even at zero load. This is a simplified individual-pile service estimate. Group settlement, consolidation and nonlinear/cyclic movement are not calculated. ROM recommends load tests for critical deformation problems; the entered movement limit remains project-specific.

**Application conditions:** Positive D, material area, E, L, nominal Qh and user limit; l1>=0; 0.5<=alpha<=1; 0<=P<Qh. Approximate individual vertical-pile service model; no group, cyclic or ultimate settlement prediction.

**References:** Puertos del Estado, ROM 0.5-05 (2005), section 3.6.9.1.1, printed p. 269; section 3.6.9.1 for applicability. Simplified individual vertical-pile service settlement. [ROM bibliography](BIBLIOGRAPHY.md#rom_piles).


<a id="pile_lateral_ultimate"></a>

## Short rigid pile - ROM lateral soil failure

**Worksheet:** Short rigid pile - ROM lateral soil failure.

### Formulation

```math
\sigma(z)=9c+3\sigma\prime_v(z)\tan^2(45^\circ+\phi/2),\quad H_{rot}=R-C_R,\quad (e+z_{CR})C_R=(e+z_R)R
```

Total overburden and groundwater -> effective stresses -> ROM limiting pressure -> exact force/moment integration -> rotation pivot and ultimate horizontal GEO resistance.

### Inputs and units

| Input |
| --- |
| Soil-contact pile width D (m) |
| Embedded pile length L (m) |
| Horizontal load height e above ground (m) |
| Unsupported upper depth (m; input required) |
| Water depth (m; blank=dry) |
| Water unit weight (kN/m3) |
| Horizontal load magnitude H (kN) |
| Required horizontal resistance factor |

**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3); Adopted cohesion c in ROM pressure law (kPa); Adopted friction angle in ROM pressure law (deg).

### Outputs and application

The general ROM Figure 3.6.12 pressure law is integrated piecewise exactly. The rotation pivot is found from moment equilibrium, with reaction and counter-reaction on opposite sides. Groundwater is hydrostatic and total soil weights must be entered. Unsupported depth removes reaction while retaining the entered overburden; actual excavation needs a correctly redefined ground/stress datum. This model is not a reproduction of the separate pure-clay Broms chart. It assumes a short structurally rigid pile: section yielding may govern first. Opposite-sign head moments, flexible-pile p-y response, group interaction, cyclic degradation and displacements require other calculations.

**Application conditions:** Short, structurally rigid vertical pile; D,L,H>0, e>=0, 0<=unsupported<L. Contiguous layers to toe, gamma,c>=0 and 0<=phi<60 degrees; hydrostatic water, nonnegative effective stress; required factor>=1. General ROM GEO model, not flexible-pile structural resistance or cyclic/lateral displacement.

**References:** Puertos del Estado, ROM 0.5-05 (2005), section 3.6.8.1, pp. 265-267, Figure 3.6.12; section 3.6.8.3, p. 268. General rigid-pile pressure model, not the digitized Broms charts. [ROM bibliography](BIBLIOGRAPHY.md#rom_piles).
