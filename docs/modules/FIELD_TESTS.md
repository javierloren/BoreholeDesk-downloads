# Field tests and pavement calculations

[Module index](../MODULES.md) · [Bibliography](BIBLIOGRAPHY.md)

Open **Computation > Calculation worksheet**, choose the named method, enter the parameters and tables, then calculate. Review the schedule and method conditions, save the case to the project and export its calculation report. The following equations describe the implemented variant; symbols are local to each method.

- [Lateral profile-test calibration and linear Winkler response](#ballast_lateral)
- [SPT energy/equipment correction and overburden normalization](#spt)
- [Schlumberger electrical sounding reduction](#ves)
- [AASHTO 1993 rigid pavement equation](#pavement_rigid)

<a id="ballast_lateral"></a>

## Lateral profile-test calibration and linear Winkler response

**Worksheet:** Subgrade reaction - calibrated lateral test.

### Formulation

```math
\begin{gathered}
EI\,y''''(z)+k_{ref}f(z/1\,m)b\,y(z)=p(z),\qquad K_i=k_{ref}f(z_i/1\,m)b h_i\\
f(\zeta)\in\left\{1,\zeta,\zeta^2,\frac{\ln(1+\zeta)}{\ln2}\right\}
\end{gathered}
```

E and I are the profile modulus and bending inertia, b soil-contact width and hi spring tributary length. The selected constant, linear, quadratic or logarithmic distribution defines a dimensionless depth shape. The test force, load height, measurement height and measured displacement calibrate kref. The design profile is then recalculated for its own EI, dimensions and ground-level shear/moment. An unsupported depth suppresses springs in that zone. Ground-displacement M–Q boundaries are service response limits, not structural bending/shear capacities.

### Inputs and units

| Input |
| --- |
| Test: embedded length (m) |
| Test: soil-contact width (m) |
| Test: bending inertia I (m4) |
| Test: elastic modulus E (MPa) |
| Test: horizontal force (kN) |
| Test: load height above ground (m) |
| Test: measurement height above ground (m) |
| Test: measured displacement (mm) |
| Unsupported depth below ground (m) |
| Subgrade distribution |
| Maximum spring tributary length (m) |
| Design: embedded length (m) |
| Design: soil-contact width (m) |
| Design: bending inertia I (m4) |
| Design: elastic modulus E (MPa) |
| Design: ground-level shear Q (kN) |
| Design: ground-level moment M (kN m) |
| Design: ground displacement limit (mm) |

### Outputs and application

Results include Calibrated k at 1 m (MN/m3); Test spring stiffness at 1 m / mesh cell (kN/m); Design spring stiffness at 1 m / mesh cell (kN/m); Fitted measured displacement (mm); Calibration residual (mm); Calibration iterations; Test ground displacement (mm); Design ground displacement (mm); Design ground rotation (rad); Ground displacement utilization; Positive-limit M at applied Q (kN m); Positive-limit Q at applied M (kN); Ground compliance a (mm/kN); Ground compliance b (mm/(kN m)); M-Q slope (m); Positive-limit moment intercept (kN m); Positive-limit shear intercept (kN); Maximum absolute nodal bending (kN m); Force equilibrium residual (kN); Moment equilibrium residual (kN m).

**Application conditions:** Positive lengths, widths, E, I, test force/displacement and design limit. 0 <= measurement height <= load height; excavation < both embedded lengths. Mesh 2..160 intervals. Linear elastic Winkler calibration; no universal transferable k range.

**References:** [beam](BIBLIOGRAPHY.md#beam).


<a id="spt"></a>

## SPT energy/equipment correction and overburden normalization

**Worksheet:** SPT - N60 and (N1)60.

### Formulation

```math
N_{60}=N\frac{ER}{60}C_BC_RC_S,\qquad (N_1)_{60}=C_NN_{60},\qquad C_N=\min\left(C_{N,max},\sqrt{\frac{P_a}{\sigma'_v}}\right)
```

N is the completed 300 mm penetration blow count, ER measured energy ratio in percent, and CB/CR/CS the adopted borehole, rod and sampler correction factors. Pa and σ′v must have the same pressure unit. The implemented normalization is the Liao–Whitman square-root form with an explicit CN cap. Supply effective stress directly or derive it from contiguous total-weight layers and hydrostatic groundwater. Partial penetration/refusal must be reviewed before entry. Corrected N is not automatically converted to strength, modulus or liquefaction resistance.

### Inputs and units

| Input |
| --- |
| Reference pressure Pa (kPa) |
| Maximum CN (Liao-Whitman) |
| Water table depth (m; blank=dry) |
| Water unit weight (kN/m3; wet profile only) |

**Samples table:** Sample depth (m); Field N (blows / 300 mm); Direct effective stress (kPa; or use Layers); Measured energy ratio ER (%); Borehole factor CB; Rod factor CR; Sampler factor CS.


**Layers table:** Top (m); Bottom (m); Total unit weight (kN/m3).


### Outputs and application

Results include Samples; Reference pressure (kPa); Maximum CN.

**Application conditions:** Depth,N >=0; reference pressure,CN cap,energy and equipment factors >0; effective stress >0 for normalization. Direct stresses OR contiguous stress layers. Full-penetration N only; refusal cannot be treated as an ordinary blow count.

**References:** [spt](BIBLIOGRAPHY.md#spt).


<a id="ves"></a>

## Schlumberger electrical sounding reduction

**Worksheet:** VES / SEV - Schlumberger sounding.

### Formulation

```math
a=AB/2,\quad b=MN/2,\qquad K=\frac{\pi(a^2-b^2)}{2b},\qquad\rho_a=K\frac{\Delta V}{I}
```

AB is current-electrode separation and MN potential-electrode separation for a symmetric collinear array, with a>b>0. The raw schedule uses voltage in mV and current in mA, whose ratio gives ohms; K is in metres and apparent resistivity ρa in Ω·m. Alternatively enter already reduced apparent resistivity. Repeated AB/2 readings are retained in the schedule. The sounding is plotted on logarithmic axes. Optional interpreted layers are user-supplied, not a fitted inversion or an automatic lithology assignment.

### Inputs and units

| Input |
| --- |
| Preferred minimum AB/MN ratio (quality note) |

**Readings table:** AB/2 (m); Apparent rho (ohm m; direct); MN/2 (m; raw); Voltage (mV; signed); Current (mA; signed).


**Interpretation table:** Interpreted top (m); Display bottom (m); Interpreted resistivity (ohm m).


### Outputs and application

Results include Readings; Minimum apparent resistivity (ohm m); Maximum apparent resistivity (ohm m).

**Application conditions:** AB/2 > MN/2 >0 for raw readings; current !=0 and apparent resistivity >0. Preferred AB/MN >1. Supply direct rho OR raw readings; interpretation layers contiguous from zero. No automatic inversion or lithology identification.

**References:** [ves](BIBLIOGRAPHY.md#ves).


<a id="pavement_rigid"></a>

## AASHTO 1993 rigid pavement equation

**Worksheet:** Rigid pavement - AASHTO 1993.

### Formulation

```math
\begin{aligned}\log_{10}W_{18}={}&Z_RS_0+7.35\log_{10}(D+1)-0.06\\&+\frac{\log_{10}(\Delta PSI/3)}{1+1.624\times10^7/(D+1)^{8.46}}\\&+(4.22-0.32p_t)\log_{10}\left[\frac{S_cC_d(D^{0.75}-1.132)}{215.63J\left(D^{0.75}-18.42/(E_c/k)^{0.25}\right)}\right]\end{aligned}
```

This is the empirical form displayed in the FDOT Rigid Pavement Design Manual (July 2004), figure 3.1. W18 is design 80 kN ESAL traffic, ZR the normal deviate for reliability, S0 overall standard deviation, ΔPSI=pi−pt serviceability loss, Sc flexural strength, Ec concrete modulus, k effective support, J load-transfer and Cd drainage coefficient. The equation kernel uses D in inches, Sc/Ec in psi and k in pci; interface SI entries are converted explicitly. The increasing equation branch is solved within the selected thickness bounds and rounded upward to the specified increment. Optional drawn subbase thickness does not automatically recalculate effective k.

### Inputs and units

| Input |
| --- |
| Design traffic W18 (80 kN ESALs) |
| Design reliability (%) |
| Overall standard deviation So |
| Initial serviceability pi |
| Terminal serviceability pt |
| Flexural strength Sc (MPa) |
| Concrete elastic modulus Ec (MPa) |
| Effective support k (MN/m3) |
| Load transfer coefficient J |
| Drainage coefficient Cd |
| Search minimum slab thickness (mm) |
| Search maximum slab thickness (mm) |
| Round thickness UP to increment (mm) |
| Subbase thickness for section view (mm; optional) |

### Outputs and application

Results include Equation thickness (mm); Rounded UP thickness (mm); Equation thickness (in); Reliability normal deviate ZR; Design log10 W18; Adopted log10 W18; Equation residual (log10 W18).

**Application conditions:** 50 <= reliability <100%; 1.5 <= terminal serviceability < initial <=4.5. Traffic,moduli,reaction,coefficients >0; 0 < search minimum < maximum and increment >0. AASHTO empirical equation; local calibration remains necessary.

**References:** [pavement](BIBLIOGRAPHY.md#pavement).


<a id="geophysical"></a>

## Measured curves and site-specific field-test comparisons

**Worksheet:** Geophysical depth log / field-test correlation.

### Formulation

For a reviewed reference observation at depth z, an exact log reading is used when
available. Otherwise interpolation uses the two adjacent finite measurements, only
when their spacing does not exceed the supplied maximum bracket:

```math
y(z)=y_0+(y_1-y_0)\frac{z-z_0}{z_1-z_0},\qquad z_0\leq z\leq z_1
```

No extrapolation or interpolation across explicit NoData is performed. Decreasing
logs are reversed only in the working copy. Original depth order, signed values and
source identifiers are retained. The user selects comparison depths and a common
material domain; the software does not infer interval midpoints or lithology.

An optional site-specific fit uses reference-test value x and measured curve y.
Linear least squares follows NIST/SEMATECH:

```math
b=\frac{\sum_i(x_i-\bar{x})(y_i-\bar{y})}{\sum_i(x_i-\bar{x})^2},\qquad a=\bar{y}-b\bar{x},\qquad \hat{y}=a+bx
```

Power fitting applies the same equations to log(x), log(y), then exponentiates the
intercept to obtain a. All paired values must be positive for a power fit.

```math
\log\hat{y}=\log a+b\log x,\qquad \hat{y}=ax^b
```

The reported residuals, RMSE and R squared use the original measured-value scale.
R squared is undefined for constant y. Repeated observations remain separate;
correlated replicates should be reviewed before fitting.

```math
RMSE=\sqrt{\frac{1}{n}\sum_i(y_i-\hat{y}_i)^2},\qquad R^2=1-\frac{\sum_i(y_i-\hat{y}_i)^2}{\sum_i(y_i-\bar{y})^2}
```

### Inputs and units

| Input |
| --- |
| Measured curve and unit |
| Reference test / unit |
| Maximum interpolation bracket (m) |
| Site-specific fit |

**Readings table:** Measured depth below common reference (m); Measured value (selected curve unit; blank = NoData); Measurement source.

**Samples table:** Reference comparison depth (m); Observed reference value (selected test / unit); Reference source / sample ID.

**Context table:** Borehole / common depth reference / provenance.

### Outputs and application

Outputs include matched/unmatched counts, a paired depth schedule, matching status
(0 unmatched, 1 exact, 2 interpolated), a common-depth figure and cross-plot.
Optional fits supply a, b, residuals, RMSE and R squared. The fitted curve is drawn
only over the observed reference range.

Use 2-10000 strictly monotonic log depths and up to 200 reviewed reference
observations from the same borehole/location and depth datum. SP and temperature
may be signed; resistivity and velocities must be positive; gamma nonnegative.
Select field N, N60, (N1)60, CPT qc or UCS explicitly; qc and UCS use positive MPa.
SPT corrections belong in the SPT worksheet. Refusal and partial penetration must
not be treated as ordinary completed-penetration N values. Fits require at least
three matched pairs and distinct reference values.

These are descriptive site-specific comparisons, not universal property laws.
Measurement conditions, lithology, sampling support and independent applicability
must be assessed before engineering interpretation. In particular, SP depends on
fluid chemistry and lithology; an anomaly alone does not establish permeability
or an aquifer. Curve measurements are not automatically transferred to design
modules or stratigraphic columns.

**References:** [Measured geophysics and least squares](BIBLIOGRAPHY.md#geophysical).
