# Deep foundations

[Module index](../../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Axial resistance of piles using the lambda method](#pile)
- [Axial pile resistance with directly selected K and Nq](#pile_sand)
- [Axial sand-pile resistance with bounded chart factors](#pile_coyle)
- [Compare diameter and embedded-length alternatives](#pile_design)
- [Compare supplied pile capacities and convert force units](#pile_comparison)
- [Converse–Labarre group efficiency](#pile_group)
- [Axial load–displacement response with supplied t-z and q-z laws](#pile_transfer)
- [Sand-derived resistance limits coupled to axial load transfer](#pile_soil_transfer)

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
