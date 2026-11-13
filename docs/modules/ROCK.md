# Structural geology and rock mass classification

[Module index](../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Lower-hemisphere Schmidt and Wulff projections](#stereonet)
- [Planar, primary intersection-line and flexural-toppling screens](#rock_kinematics)
- [Geometry and strict gravity-release screening of an explicit tetrahedron](#tunnel_wedge)
- [RMR 1989 for tunnels and mines](#rmr89)
- [RMR14 with reviewed input ratings and correction factors](#rmr14)
- [Discrete Slope Mass Rating](#smr)
- [Quantified GSI using RQD and joint condition](#gsi_quantified)
- [Q index and equivalent dimension](#q_system)

<a id="stereonet"></a>

## Lower-hemisphere Schmidt and Wulff projections

**Worksheet:** Discontinuities - Schmidt / Wulff.

### Formulation

```math
\begin{gathered}
\mathbf v=(\cos p\sin t,\ \cos p\cos t,\ \sin p)\\
(X,Y)_{Schmidt}=\frac{(v_E,v_N)}{\sqrt{1+v_D}},\qquad (X,Y)_{Wulff}=\frac{(v_E,v_N)}{1+v_D}
\end{gathered}
```

t is line trend clockwise from north and p plunge downward. The vector axes are east, north, down. For a plane with dip direction d and dip β, its lower pole has trend d+180° and plunge 90°−β. An east-positive azimuth correction is added once. Great circles and pole coordinates are plotted in a unit primitive. Plane intersections use normalized cross products of their normals; parallel/coincident pairs have no unique intersection. Choose Schmidt for area preservation or Wulff for angle preservation; enter dip direction rather than strike.

### Inputs and units

| Input |
| --- |
| Projection |
| Azimuth correction, east positive (deg) |

**Planes table:** Dip direction (deg); Dip (deg).


### Outputs and application

Results include Measured planes; Nonparallel pair intersections; Parallel pairs excluded.
Enter one manually selected family per case. For two or more planes, the worksheet
reports the mean dip direction, mean dip and mean pole resultant length, and
marks the mean pole on the stereonet. The mean is obtained by summing equally
weighted lower-hemisphere unit poles after the azimuth correction. A horizontal
mean plane has no dip direction. A vanishing resultant leaves the mean undefined.
Use separate cases for mixed families.

**Application conditions:** Projection: Schmidt 0 / Wulff 1. Dip direction 0..360 deg, dip 0..90 deg, azimuth correction -180..180 deg. Lower hemisphere; 1..200 planes per case.

**References:** [structural](BIBLIOGRAPHY.md#structural).


<a id="rock_kinematics"></a>

## Planar, primary intersection-line and flexural-toppling screens

**Worksheet:** Rock station - planar / wedge-line / flexural toppling screen.

### Formulation

```math
\tan\beta_{app}=\tan\beta_{face}\cos\Delta d,\qquad \phi_j\lt \beta_j\lt \beta_{app}
```

The inequality describes the planar angular screen, together with the selected lateral-direction half-width. βface is face dip, Δd directional separation, βj joint dip and φj adopted common friction. The primary wedge-line screen requires intersection plunge above friction and below apparent face dip in the intersection direction. Flexural toppling uses inward-dipping joints and a positive margin between apparent (face dip−friction) and pole plunge. Strict angular inequalities define candidates; equality is a boundary. Counts are geometric candidates, not failure probabilities or factors of safety.

### Inputs and units

| Input |
| --- |
| Projection |
| Azimuth correction, east positive (deg) |
| Station X (m, project/local grid) |
| Station Y (m, same grid) |
| Station elevation (m, stated datum) |
| Face dip direction (corrected deg) |
| Face dip (deg) |
| Adopted joint friction angle (deg) |
| Planar / toppling lateral half-width (deg) |

**Planes table:** Dip direction (deg); Dip (deg).


### Outputs and application

Results include Measured planes; Nonparallel pair intersections; Parallel pairs excluded; Planar screen candidates; Flexural toppling screen candidates; Primary wedge-line screen candidates.

**Application conditions:** One named station, 1..100 planes; direction 0..360, dip 0..90; 0<face dip<90, 0<=friction<90, 0<lateral half-width<90. Common friction, planar face. Primary wedge-line and flexural toppling screens only; no safety conclusion from zero flags.

**References:** [rock_slope](BIBLIOGRAPHY.md#rock_slope), [structural](BIBLIOGRAPHY.md#structural).


<a id="tunnel_wedge"></a>

## Geometry and strict gravity-release screening of an explicit tetrahedron

**Worksheet:** Tunnel wedge - explicit tetrahedron.

### Formulation

```math
V=\frac{|(B-A)\cdot[(C-A)\times(D-A)]|}{6},\quad W=\gamma V,\quad G=\frac{A+B+C+D}{4}
```

A, B and C define the planar excavation opening; D is the rock apex. Coordinates are east, north, elevation up in metres. γ is rock unit weight. Face areas and inward normals are calculated from cross products. The release test checks whether downward movement opens all three joint contacts and exits the excavation face strictly. A zero flag means this strict free-release condition is unresolved; sliding/contact resistance requires a separate analysis. The supplied block geometry and discontinuity persistence must be reviewed against the excavation.

### Inputs and units

| Input |
| --- |
| Rock unit weight (kN/m3) |

**Vertices table:** East X (m); North Y (m); Elevation Z (m).


### Outputs and application

Results include Volume (m3); Weight (kN); Centroid east (m); Centroid north (m); Centroid elevation (m); Strict gravity free release (1=yes, 0=unresolved).

**Application conditions:** Exactly 4 finite, non-coplanar vertices; gamma >0. Vertices 1..3 define the excavation face, vertex 4 the rock apex. Geometry/gravity-release screening only; no frictional FS or support design.

**References:** [structural](BIBLIOGRAPHY.md#structural), [wedge](BIBLIOGRAPHY.md#wedge).


<a id="rmr89"></a>

## RMR 1989 for tunnels and mines

**Worksheet:** RMR 1989 - tunnels and mines.

### Formulation

```math
RMR_{basic}=R_{strength}+R_{RQD}+R_{spacing}+R_{condition}+R_{water},\qquad RMR=RMR_{basic}+\Delta R_{orientation}
```

The worksheet assigns the RMR89 strength, RQD, spacing, joint-condition and groundwater ratings from the entered observations. Strength uses UCS or corrected point-load index Is(50) with its applicable range. Detailed joint condition sums persistence, aperture, roughness, weathering and a no-infill contribution; filled joints use the overall A.4 selection. The selected tunnel/mine orientation adjustment is applied separately. Shared numerical endpoints use the lower rating. Review each contribution before accepting the resulting class.

### Desktop workflow

Open **RMR rating guide** to inspect the rating ranges. Select a categorical
description to apply it to the case; selecting a numeric parameter opens its
measured input without assigning a representative value. The guide highlights
the current valid calculation. Editing inputs clears these highlights until
the case is recalculated.

Use **Export RMR card PNG...** for a 300 dpi classification sheet containing
the measurements, component scores, basic and corrected RMR, rock class and
bibliographic reference. The numerical total is retained even when negative.
The existing calculation PDF includes the full input record and method notes.
Both exports require a current valid result.

### Inputs and units

| Input |
| --- |
| Strength test |
| Intact rock strength / index (MPa) |
| RQD (%) |
| Discontinuity spacing (m) |
| Joint condition method |
| Persistence category |
| Aperture category |
| Roughness category |
| Weathering category |
| Overall A.4 rating (overall mode only) |
| Observed groundwater |
| Orientation relative to tunnel / mine drive |

### Outputs and application

Results include RMR basic; Orientation correction; RMR corrected (unclipped); Rock class (I=1 ... V=5).

**Application conditions:** RMR89 table method, tunnels/mines only. Positive UCS or Is(50)>1 MPa; RQD 0..100%; spacing >0 m. Explicit category selection. Detailed joint mode assumes no infill; filled joints require overall A.4 assessment. No support or stability design.

**References:** [rmr89](BIBLIOGRAPHY.md#rmr89).


<a id="rmr14"></a>

## RMR14 with reviewed input ratings and correction factors

**Worksheet:** RMR14 - reviewed ratings and factors (Celada et al. 2014).

### Formulation

```math
RMR_{14}=(RMR_{14,basic}+F_0)F_eF_s
```

The basic value sums supplied strength, discontinuity-frequency and joint-condition ratings plus durability and groundwater ratings. The durability input is second-cycle Id2; F0 is the selected orientation correction, Fe excavation adjustment and Fs stress/yielding adjustment. Ratings must be read and justified using the RMR14 edition, rather than reusing RMR89 bins. The adjusted result is retained without clipping. Input ratings are not raw UCS, joint count or automatically inferred ICE.

### Inputs and units

| Input |
| --- |
| Reviewed UCS rating (0..15) |
| Reviewed joints/metre rating (0..40) |
| Reviewed RMR14 joint-condition rating (0..20) |
| Slake durability Id2 (%) |
| Groundwater category |
| Tunnel orientation adjustment F0 |
| Reviewed excavation factor Fe (1..1.32) |
| Reviewed face yielding factor Fs (>0, <=1) |

### Outputs and application

Results include RMR14 basic; Alterability rating; F0; Fe; Fs; RMR14 adjusted (unclipped).

**Application conditions:** Supplied ratings: strength 0..15, joint frequency 0..40, joint condition 0..20. Id2 0..100%; explicit water/F0 category; Fe 1..1.32 and 0<Fs<=1. Assisted worksheet; raw-observation curves and ICE are not implemented.

**References:** [rmr14](BIBLIOGRAPHY.md#rmr14).


<a id="smr"></a>

## Discrete Slope Mass Rating

**Worksheet:** SMR - Romana discrete planar / toppling.

### Formulation

```math
SMR=RMR_{89,basic}+F_1F_2F_3+F_4
```

F1 describes the joint/face directional relation, F2 the relevant joint dip, F3 the dip relation for the selected planar or toppling mode, and F4 the selected excavation category. The worksheet uses the discrete formulation in the cited tables. For planar mode C=joint dip−face dip; for toppling C=their sum. The method reports the factors and rating stages. Shared F1/F2 endpoints use the more adverse factor; assess measurements near bin boundaries. SMR is a classification, not force equilibrium.

### Inputs and units

| Input |
| --- |
| RMR89 basic BEFORE orientation (0..100) |
| Mechanism to assess |
| Slope dip direction (deg from north) |
| Slope dip (deg) |
| Joint dip direction (deg from north) |
| Joint dip (deg) |
| Excavation method |

### Outputs and application

Results include A angular separation (deg); B joint dip (deg); C dip relation (deg); F1; F2; F3; F4; SMR (unclipped).

**Application conditions:** RMR89 basic 0..100, dip directions 0..360 deg, dips 0..90 deg; explicit planar/toppling mode and excavation category. Discrete factors; no wedge extension, support or FS.

**References:** [smr](BIBLIOGRAPHY.md#smr).


<a id="gsi_quantified"></a>

## Quantified GSI using RQD and joint condition

**Worksheet:** GSI - Hoek, Carter and Diederichs 2013.

### Formulation

```math
GSI=1.5JCond_{89}+\frac{RQD}{2}
```

JCond89 is the RMR89 joint-condition rating (0–30); RQD is a reviewed percentage. This is the quantified 2013 estimate, not a digital reproduction of a visual GSI chart. Confirm the applicability to a sufficiently jointed, effectively homogeneous/isotropic blocky mass before calculation. The two contributions are shown separately. The result does not automatically determine Hoek–Brown material constants.

### Inputs and units

| Input |
| --- |
| Reviewed RQD (%) |
| Joint-condition rating JCond89 (0..30) |
| Rock mass applicability |

### Outputs and application

Results include Quantified GSI estimate; Joint-condition contribution; RQD contribution.

**Application conditions:** RQD 0..100%, JCond89 0..30, explicit confirmation of blocky/homogeneous/isotropic applicability. Quantified GSI estimate 0..95, not a universal visual-chart replacement.

**References:** [gsi](BIBLIOGRAPHY.md#gsi).


<a id="q_system"></a>

## Q index and equivalent dimension

**Worksheet:** Q index - NGI handbook 2025 (supplied factors).

### Formulation

```math
Q=\frac{\max(10,RQD)}{J_n}\frac{J_r}{J_a}\frac{J_w}{SRF},\qquad D_e=\frac{span}{ESR}
```

Jn is joint-set number, Jr roughness number, Ja alteration number, Jw water reduction and SRF stress reduction. ESR is the adopted excavation support ratio and span is in metres. The minimum RQD of 10 is a Q-calculation convention; it does not overwrite the observed RQD. Factors are supplied using the applicable NGI 2025 guidance and displayed by contribution. Selecting rock support requires the handbook conditions and engineering assessment, beyond this index calculation.

### Inputs and units

| Input |
| --- |
| Measured RQD (%) |
| Adopted joint-set number Jn |
| Joint roughness number Jr |
| Joint alteration number Ja |
| Joint water factor Jw |
| Stress reduction factor SRF |
| Excavation span / wall height (m) |
| Selected excavation support ratio ESR |

### Outputs and application

Results include Q; Observed RQD (%); RQD used in Q (%); RQD/Jn; Jr/Ja; Jw/SRF; Equivalent dimension (m).

**Application conditions:** RQD 0..100% (adopted minimum 10 for Q only); positive Jn,Jr,Ja,Jw,SRF,span,ESR; Jw<=1. Factors selected from applicable NGI 2025 guidance; no automatic support design.

**References:** [q](BIBLIOGRAPHY.md#q).


<a id="rock_modulus"></a>

## Isotropic rock-mass deformation modulus

**Worksheet:** Rock mass modulus - Hoek-Diederichs 2006.

### Formulation

With no reliable intact modulus supplied, the worksheet uses Hoek and Diederichs
(2006), equation 2, with Erm in MPa:

```math
E_{rm}=100000\frac{1-D/2}{1+\exp[(75+25D-GSI)/11]}
```

Supplying intact Ei in MPa selects equation 4 instead:

```math
E_{rm}=E_i\left[0.02+\frac{1-D/2}{1+\exp[(60+15D-GSI)/11]}\right]
```

### Inputs and units

| Input |
| --- |
| Reviewed GSI (0..100) |
| Disturbance factor D (0..1) |
| Intact modulus Ei (MPa; blank = simplified Eq. 2) |
| Isotropic rock mass applicability |

### Outputs and application

The worksheet reports Erm in MPa, GPa and kPa and shows sensitivity to D.
Curves are not confidence intervals. GSI must describe the assessed rock mass;
D represents adopted excavation damage/stress relaxation. Ei is an intact-rock
modulus, not the macroscopic rock-mass modulus. The correlations assume effective
isotropy; directional schistose behaviour needs another model. Review applicability
at the excavation scale. Erm is not a strength parameter, dynamic wave modulus,
constrained modulus M or subgrade reaction k. It is not applied automatically to
another calculation.

**References:** [Hoek and Diederichs (2006)](BIBLIOGRAPHY.md#rock_modulus).


<a id="hoek_brown"></a>

## Rock mass strength - generalized Hoek-Brown

**Worksheet:** Rock mass strength - generalized Hoek-Brown.

### Formulation

Generalized Hoek-Brown constants and compression strength follow the 2002
formulation retained in the 2018 edition published by Hoek and Brown (2019):

```math
m_b=m_i\exp\!\left(\frac{GSI-100}{28-14D}\right),\quad s=\exp\!\left(\frac{GSI-100}{9-3D}\right),\quad a=\frac12+\frac{e^{-GSI/15}-e^{-20/3}}6
```

```math
\sigma'_1=\sigma'_3+\sigma_{ci}\left(m_b\frac{\sigma'_3}{\sigma_{ci}}+s\right)^a,\qquad \sigma_c=\sigma_{ci}s^a
```

Compression is positive; stresses use MPa. The plotted principal branch is
0 to the adopted maximum effective confinement. Balmer's transformation uses
q=d sigma1/d sigma3 to obtain the shear-envelope coordinates:

```math
q=1+a m_b\left(m_b\sigma'_3/\sigma_{ci}+s\right)^{a-1},\quad \sigma'_n=\sigma'_3+\frac{\sigma'_1-\sigma'_3}{1+q},\quad \tau=\frac{(\sigma'_1-\sigma'_3)\sqrt q}{1+q}
```

Equivalent Mohr-Coulomb parameters use equations 12-13 of Hoek et al. (2002).
Let x=sigma3max/sigma_ci, t=s+mb*x, B=(1+a)(2+a) and K=a*mb*t^(a-1):

```math
\phi'=\arcsin\!\left(\frac{6K}{2B+6K}\right),\qquad c'=\frac{\sigma_{ci}[(1+2a)s+(1-a)m_bx]t^{a-1}}{B\sqrt{1+6K/B}}
```

This is the **2002 range fit**, with formal lower cutoff -sigma_ci*s/mb and
upper sigma3max. It is not an instantaneous tangent, universal c/phi or a tensile
constitutive model. The two figures distinguish the compression and shear
coordinates. The lower cutoff is reported as the fit definition only.

### Inputs and units

| Input |
| --- |
| Intact UCS sigma_ci (MPa) |
| Intact constant mi |
| Reviewed GSI (0..100) |
| Disturbance D (0..1) |
| Maximum effective confinement sigma3 (MPa) |
| Brittle isotropic rock mass applicability |

### Outputs and application

Positive sigma_ci, mi and maximum confinement; GSI 0..100 and D 0..1. Confirm representative brittle, effectively isotropic rock-mass behaviour at the assessment scale and a justified confinement range. Individual blocks/wedges, intact spalling and ductile/high-confinement behaviour need other models. No automatic transfer of equivalent parameters to slope cases.

**References:** [hoek_brown](BIBLIOGRAPHY.md#hoek_brown).


<a id="barton_joint"></a>

## Joint peak strength - Barton JRC-JCS

**Worksheet:** Joint peak strength - Barton JRC-JCS.

### Formulation

For adopted field-scale JRC, joint-wall strength JCS and residual friction phi_r,
the Barton-Choubey peak envelope is:

```math
\sigma'_{n}=\sigma_n-u,\qquad \tau_p=\sigma'_n\tan\!\left[\phi_r+JRC\log_{10}\!\left(\frac{JCS}{\sigma'_n}\right)\right]
```

Angles use degrees and all stresses use MPa. No added cohesion is used. For
nonpositive effective normal stress the worksheet credits zero frictional
resistance. Residual friction resistance is sigma_n_eff*tan(phi_r), without
roughness. No tensile strength or joint opening displacement is calculated.

Optional paired block lengths apply the empirical scale laws discussed by
Barton (2013). Both exponents use the **original** reference-scale JRC0:

```math
JRC_n=JRC_0(L_n/L_0)^{-0.02JRC_0},\qquad JCS_n=JCS_0(L_n/L_0)^{-0.03JRC_0}
```

Leave both lengths blank for already adopted field-scale parameters. Supply both
positive lengths with Ln at least L0 to apply scaling once. L refers to the
assessed block scale, not automatically the total joint trace.

### Inputs and units

| Input |
| --- |
| Joint roughness JRC (0..20) |
| Joint wall strength JCS (MPa) |
| Residual friction phi_r (deg) |
| Reference block length L0 (m; optional) |
| Assessment block length Ln (m; optional) |
| Unfilled contacting joint applicability |

**Stresses table:** Total normal stress (MPa); Water pressure (MPa; blank = 0); Stress / parameter source.

### Outputs and application

JRC 0..20; JCS positive; residual friction 0..less than 90 degrees. Confirm matching unfilled joint walls and appropriate field scale. Implementation excludes effective compression above adopted JCS and apparent peak angles of 90 degrees or more; it does not silently clip either. High apparent angles require review of low-stress extrapolation. Stress rows retain source order, while plotted copies are sorted; lines only connect supplied states. No filled-joint, deformation or slope safety-factor model.

**References:** [barton_joint](BIBLIOGRAPHY.md#barton_joint).
