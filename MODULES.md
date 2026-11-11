# BoreholeDesk module reference

BoreholeDesk combines field records, borehole interpretation and explicit engineering methods in a local desktop project. This reference covers the **36 calculation worksheets**, slope stability methods and data-to-report workflows available in the desktop.

[User guide](USER_GUIDE.md) · [Bibliography](modules/BIBLIOGRAPHY.md)

## Calculation worksheets

Choose the exact method and edition for the question being assessed. Check the input basis, units, groundwater, geometry and safety-factor convention before comparing alternatives. Each method card lists its actual input schedule, equations, outputs and application conditions.

### Shallow foundations and settlement

| Worksheet | Method reference |
| --- | --- |
| Undrained bearing capacity | [Undrained footing resistance with biaxial eccentricity](modules/FOUNDATIONS.md#bearing) |
| Drained bearing - Vesic factors / FHWA shape | [General-shear footing resistance using effective stresses](modules/FOUNDATIONS.md#bearing_drained) |
| Footing contact - uniaxial compression only | [Uniaxial compression-only footing contact](modules/FOUNDATIONS.md#footing_contact) |
| Foundation alternatives - supplied pressures and settlements | [Compare supplied pressures and observed or supplied settlements](modules/FOUNDATIONS.md#foundation_service) |
| Stress and consolidation | [Stress increments and one-dimensional primary consolidation](modules/FOUNDATIONS.md#settlement) |
| Settlement field - Boussinesq / 1D primary consolidation | [Plan and section views of primary consolidation](modules/FOUNDATIONS.md#settlement_field) |
| Immediate settlement - elastic layered field | [Vertical elastic-strain integration through layers](modules/FOUNDATIONS.md#settlement_elastic) |
| Schmertmann - square footing | [Square-footing settlement with the fixed influence diagram](modules/FOUNDATIONS.md#schmertmann) |
### Deep foundations

| Worksheet | Method reference |
| --- | --- |
| Pile axial capacity - lambda | [Axial resistance of piles using the lambda method](modules/PILES.md#pile) |
| Sand - K tan(delta), direct Nq | [Axial pile resistance with directly selected K and Nq](modules/PILES.md#pile_sand) |
| Sand - Coyle-Castello chart tables | [Axial sand-pile resistance with bounded chart factors](modules/PILES.md#pile_coyle) |
| Sand - diameter / length design table | [Compare diameter and embedded-length alternatives](modules/PILES.md#pile_design) |
| Capacity table and unit conversion | [Compare supplied pile capacities and convert force units](modules/PILES.md#pile_comparison) |
| Pile group - Converse-Labarre screening | [Converse–Labarre group efficiency](modules/PILES.md#pile_group) |
| Pile axial load-transfer - supplied t-z / q-z laws | [Axial load–displacement response with supplied t-z and q-z laws](modules/PILES.md#pile_transfer) |
| Sand axial response - beta / Nq and load transfer | [Sand-derived resistance limits coupled to axial load transfer](modules/PILES.md#pile_soil_transfer) |
### Earth pressure and excavation checks

| Worksheet | Method reference |
| --- | --- |
| Cohesive earth pressure | [Undrained cohesive earth pressure with a tension cut-off](modules/EARTH_PRESSURE.md#pressure) |
| Rankine / Jaky - dry or groundwater | [Rankine and normally consolidated at-rest pressure](modules/EARTH_PRESSURE.md#pressure_drained) |
| Coulomb active - dry inclined wall/backfill | [Coulomb active resultant for an inclined wall and backfill](modules/EARTH_PRESSURE.md#pressure_coulomb) |
| At rest - Jaky / OCR / elastic comparison | [Compare at-rest pressure hypotheses](modules/EARTH_PRESSURE.md#pressure_k0) |
| Rankine-Bell active - layered effective stresses | [Local Rankine–Bell active pressure in layered effective-stress ground](modules/EARTH_PRESSURE.md#pressure_layered) |
| At-rest pressure - layered effective stresses | [At-rest pressure for a restrained wall in layered ground](modules/EARTH_PRESSURE.md#pressure_k0_layered) |
| Excavation screening checks | [Basal bearing analogy and hydraulic plug uplift](modules/EARTH_PRESSURE.md#excavation) |
### Structural geology and rock mass classification

| Worksheet | Method reference |
| --- | --- |
| Discontinuities - Schmidt / Wulff | [Lower-hemisphere Schmidt and Wulff projections](modules/ROCK.md#stereonet) |
| Rock station - planar / wedge-line / flexural toppling screen | [Planar, primary intersection-line and flexural-toppling screens](modules/ROCK.md#rock_kinematics) |
| Tunnel wedge - explicit tetrahedron | [Geometry and strict gravity-release screening of an explicit tetrahedron](modules/ROCK.md#tunnel_wedge) |
| RMR 1989 - tunnels and mines | [RMR 1989 for tunnels and mines](modules/ROCK.md#rmr89) |
| RMR14 - reviewed ratings and factors (Celada et al. 2014) | [RMR14 with reviewed input ratings and correction factors](modules/ROCK.md#rmr14) |
| SMR - Romana discrete planar / toppling | [Discrete Slope Mass Rating](modules/ROCK.md#smr) |
| GSI - Hoek, Carter and Diederichs 2013 | [Quantified GSI using RQD and joint condition](modules/ROCK.md#gsi_quantified) |
| Q index - NGI handbook 2025 (supplied factors) | [Q index and equivalent dimension](modules/ROCK.md#q_system) |
### Field tests and pavement calculations

| Worksheet | Method reference |
| --- | --- |
| Subgrade reaction - calibrated lateral test | [Lateral profile-test calibration and linear Winkler response](modules/FIELD_TESTS.md#ballast_lateral) |
| SPT - N60 and (N1)60 | [SPT energy/equipment correction and overburden normalization](modules/FIELD_TESTS.md#spt) |
| VES / SEV - Schlumberger sounding | [Schlumberger electrical sounding reduction](modules/FIELD_TESTS.md#ves) |
| Rigid pavement - AASHTO 1993 | [AASHTO 1993 rigid pavement equation](modules/FIELD_TESTS.md#pavement_rigid) |
### Finite elements

| Worksheet | Method reference |
| --- | --- |
| FEM - elastic plane-strain ground block (incremental) | [Incremental linear plane-strain elasticity with constant-strain triangles](modules/FINITE_ELEMENTS.md#fem_elastic) |

## Slope stability

[Slope methods, groundwater, circular search and active tiebacks](modules/SLOPES.md). Includes Ordinary/Fellenius, Bishop simplified, Janbu simplified, Spencer and Morgenstern–Price.

## Field records, interpretation and reporting

[Projects, boreholes, OCR, core photographs/RQD, sections, locations, samples, data checks and reports](modules/WORKFLOWS.md).

## Working with calculation cases

Save the case inputs and the field or test evidence used to select parameters. Recalculate after changes and review intermediate schedules before exporting. Clearly identify observed values, adopted parameters and interpretations. Separate numerical verification of a method from its suitability for a particular site.

The explanations and equation notation in this reference describe BoreholeDesk. Referenced books, reports and scientific papers remain with their authors and publishers; source figures, private workbooks and commercial software are not reproduced here. Software/model licences and required attributions are listed in [Third-party notices](THIRD_PARTY_NOTICES.md).
