# Technical bibliography

[Module index](../MODULES.md)

Method cards identify the specific formulation and application conditions used
by BoreholeDesk. The references below establish the scientific or engineering
basis; a reference to a publication or software theory manual is not a claim of
certification, endorsement or numerical equivalence with another product.
Equations are presented in the notation used to explain the implementation.
Original books, figures, graphical charts and private workbooks are not reproduced.

<a id="gec6"></a>
## Shallow foundations and contact pressure

Kimmerling, R. E. (2002). *Geotechnical Engineering Circular No. 6: Shallow
Foundations*, FHWA-SA-02-054. Bearing resistance: chapter 5, tables 5-1/5-2 and
equation 5-14. Eccentric loading/contact: section 6.6, figure 6-6 and equations
6-9 to 6-13. [FHWA report](https://highways.dot.gov/media/3156).

<a id="biaxial_contact"></a>
## Biaxial footing contact

Bellos, J. and Bakas, N. P. (2016). *High Computational Efficiency through
Generic Analytical Formulation for Linear Soil Pressure Distribution of Rigid
Spread Rectangular Footings*. ECCOMAS, section 5.4 and equations 41–43.
[Conference paper](https://www.eccomas2016.org/proceedings/pdf/5100.pdf).

<a id="settlement"></a>
## Stress distribution and primary consolidation

U.S. Army Corps of Engineers (1990). *Settlement Analysis*, EM 1110-1-1904,
stress-distribution methods in appendix C and consolidation procedures in the
manual. Boussinesq superposition and base-10 compression/recompression equations.
[USACE manual](https://www.publications.usace.army.mil/Portals/76/Publications/EngineerManuals/EM_1110-1-1904.pdf).

<a id="elastic_columns"></a>
## Vertical elastic-strain integration

*Settle3 Settlement and Consolidation Theory Manual*, section 3.1, elastic-strain
framework. BoreholeDesk integrates rectangular-load stress increments through
independent layers with supplied constrained moduli and a fixed-bottom condition.
This citation identifies the public theoretical framework, not the proprietary
solver. [Theory manual](https://static.rocscience.cloud/assets/verification-and-theory/Settle3/Settle3-Settlement-and-Consolidation-Theory-Manual.pdf).

<a id="sand_stiffness"></a>
## Preliminary soil stiffness references

FHWA (2010), *Drilled Shafts: Construction Procedures and LRFD Design Methods*,
FHWA-NHI-10-016, Table 3-6, p. 3-17 (after AASHTO 2007). The input guide converts
the Young modulus ranges for sand and fine sand from ksf to kPa and rounds to
the nearest 100 kPa. Select the design modulus for the site and the working
strain. Where the worksheet requires constrained modulus M, use site data
or justify an isotropic elastic conversion.
[FHWA manual](https://highways.fhwa.dot.gov/sites/fhwa.dot.gov/files/FHWA-NHI-10-016_0.pdf).

<a id="schmertmann"></a>
## Strain-influence settlement

Schmertmann, J. H. (1970). *Static Cone to Compute Static Settlement Over Sand*,
Journal of the Soil Mechanics and Foundations Division, 96(SM3), 1011–1043.
[TRB bibliographic record](https://trid.trb.org/View/127596).
For a comparison of modified formulations, see FHWA-HRT-15-080 (2016), chapter 4,
section 4.1.1. The BoreholeDesk card states its fixed influence diagram explicitly;
it is not labelled as the modified stress-dependent-peak method.
[FHWA discussion](https://www.fhwa.dot.gov/publications/research/infrastructure/structures/bridge/15080/004.cfm).

<a id="gec10"></a>
## Deep foundations and axial response

Brown, D. A., Turner, J. P., Castelli, R. J., and Loehr, J. E. (2018).
*Drilled Shafts: Construction Procedures and Design Methods*, GEC 10,
FHWA-NHI-18-024. Chapter 10: axial resistance; appendix C: axial
load–deformation framework. Hyperbolic laws and their calibration parameters
are identified explicitly in the BoreholeDesk method cards.
[FHWA manual](https://www.fhwa.dot.gov/engineering/geotech/nhi18024.pdf).

<a id="lambda"></a>
## Lambda shaft-resistance method

NCHRP Project 24-17, appendix D, *Design of Drilled Shafts*, pp. 29–30:
lambda shaft-resistance and toe-resistance methods.
[TRB appendix](https://onlinepubs.trb.org/onlinepubs/nchrp/docs/NCHRP24-17_AppendixD.pdf).

<a id="coyle"></a>
## Piles in sand and chart factors

Coyle, H. M., and Castello, R. R. (1981). *New Design Correlations for Piles in
Sand*. Journal of the Geotechnical Engineering Division, 107(7), 965–986.
[Original article](https://doi.org/10.1061/AJGEB6.0001172).
The BoreholeDesk chart variant uses a bounded numerical approximation and
logarithmic interpolation; its ranges are stated on the method card. Direct
coefficient entry is a separate method. Neither variant automatically establishes
the suitability of a driven-pile correlation for a different construction method.

<a id="group"></a>
## Pile-group efficiency

Washington State Department of Transportation, Research Report WA-RD 827.1,
equations 2.28–2.29: Converse–Labarre group-efficiency expression.
[WSDOT report](https://www.wsdot.wa.gov/research/reports/fullreports/827.1.pdf).

<a id="si_units"></a>
## Force-unit conversion

Bureau International des Poids et Mesures. *The International System of Units
(SI)*, 9th edition. The tonne-force conversion uses standard gravity
9.80665 m/s²: 1 tf = 9.80665 kN.
[SI Brochure](https://www.bipm.org/en/publications/si-brochure).

<a id="earth"></a>
## Earth pressures

U.S. Army Corps of Engineers (1989). *Retaining and Flood Walls*,
EM 1110-2-2502, chapter 3: Rankine pressure and tension cracks.
[1989 manual](https://www.publications.usace.army.mil/portals/76/publications/engineermanuals/em_1110-2-2502.pdf).
The effective-stress, layered and hydrostatic conventions actually evaluated by
the application are stated in the individual method cards.

<a id="coulomb"></a>
## Coulomb active pressure

FHWA (2023), FHWA-HIF-24-002, *Design and Construction of Mechanically
Stabilized Earth (MSE) Walls*, Coulomb expressions, equations 18–19.
The BoreholeDesk card defines the wall/backfill angles and the horizontal-area
surcharge convention used in its force calculation.
[FHWA report](https://www.fhwa.dot.gov/engineering/geotech/pubs/hif24002.pdf).

<a id="at_rest"></a>
## At-rest pressure

Mayne, P. W., and Kulhawy, F. H. (1982). *K0–OCR Relationships in Soil*.
Journal of the Geotechnical Engineering Division, 108(GT6), 851–872.
Also USACE (2022), EM 1110-2-2502, equations 6.9–6.11.
[USACE 2022 manual](https://www.publications.usace.army.mil/Portals/76/Users/182/86/2486/EM%201110-2-2502.pdf).
Jaky normally consolidated, OCR-adjusted and elastic constrained coefficients
are separate hypotheses in the application.

<a id="structural"></a>
## Orientation geometry and stereographic projection

Allmendinger, R. W., Cardozo, N., and Fisher, D. M. (2012).
*Structural Geology Algorithms: Vectors and Tensors*. Cambridge University Press.
Vector representation, projections, normals and intersections underpin the
documented orientation geometry.
[Publisher and DOI](https://doi.org/10.1017/CBO9780511920202).

<a id="rock_slope"></a>
## Rock-slope kinematics

Goodman, R. E. (1980). *Introduction to Rock Mechanics*. Wiley.
Wyllie, D. C., and Mah, C. W. (2004). *Rock Slope Engineering*, 4th edition.
Stereographic planar/wedge and flexural-toppling conditions. The method card
identifies the angular screens implemented and distinguishes them from equilibrium.

<a id="wedge"></a>
## Explicit rock-block geometry

*UnWedge Theory Manual*, wedge geometry discussion.
[Public theory manual](https://static.rocscience.cloud/assets/verification-and-theory/UnWedge/Unwedge-Theory-Manual.pdf).
BoreholeDesk accepts an explicit tetrahedron and evaluates its geometry and a
strict gravity-release condition. It does not reproduce the UnWedge analysis engine.

<a id="rmr89"></a>
## RMR 1989

Bieniawski, Z. T. (1989). *Engineering Rock Mass Classifications: A Complete Manual
for Engineers and Geologists in Mining, Civil, and Petroleum Engineering*. Wiley,
geomechanics classification tables. The application uses the tunnel/mine
orientation adjustment and explicitly selected joint-condition modes.
[Publisher record](https://www.wiley-vch.de/en/areas-interest/natural-sciences/engineering-rock-mass-classifications-978-0-471-60172-2).

<a id="rmr14"></a>
## RMR14

Celada, B., Tardáguila, I., Varona, P., Rodríguez, A., and Bieniawski, Z. T. (2014).
*Innovating Tunnel Design by an Improved Experience-based RMR System*.
World Tunnel Congress 2014, equation 1 and table 5.
[Authors' publication](https://geocontrol.es/wp-content/uploads/2026/03/20_2014_GEOCONTROL_Celada-Tardaguila-Varona-Rodriguez-Bieniawski_RMR-System.pdf).

<a id="smr"></a>
## Slope Mass Rating

Romana, M., Tomás, R., and Serón, J. B. (2015). *Slope Mass Rating (SMR)
geomechanics classification: thirty years review*. 13th ISRM International
Congress, tables 1–2, original discrete formulation.
[Author-hosted publication](https://www.researchgate.net/publication/283584139_Slope_Mass_Rating_SMR_geomechanics_classification_thirty_years_review).

<a id="gsi"></a>
## Quantified GSI

Hoek, E., Carter, T. G., and Diederichs, M. S. (2013).
*Quantification of the Geological Strength Index Chart*, ARMA 13-672,
equation 1 and applicability discussion.
[Paper](https://www.rocscience.com/assets/resources/learning/hoek/Quantification-of-the-GSI-Chart-2013.pdf).

<a id="q"></a>
## Q-system

Norwegian Geotechnical Institute (April 2025). *Using the Q-system: Rock Mass
Classification and Support Design*. Q equation, parameter selection,
RQD minimum convention and equivalent dimension.
[NGI handbook](https://www.ngi.no/globalassets/bilder/forskning-og-radgivning/bygg-og-anlegg/q-handbook_2025_english_final.pdf).

<a id="beam"></a>
## Lateral beam and subgrade reaction

Caltrans, *Effects of Soil Slope on Lateral Capacity of Piles*, section 2.1,
equations 2.1–2.2: beam/soil interaction framework.
[Caltrans report](https://dot.ca.gov/-/media/dot-media/programs/research-innovation-system-information/documents/f0016560-final-report-task-0932.pdf).
The BoreholeDesk card states its linear Euler–Bernoulli/Winkler model,
depth distributions and test-based calibration explicitly.

<a id="fem"></a>
## Finite elements

Liu, G. R., and Quek, S. S. (2003). *The Finite Element Method: A Practical
Course*. Butterworth-Heinemann, chapters 2, 3 and 7: discretization, element
assembly and elasticity.
[Publisher record](https://www.sciencedirect.com/book/9780750658669/finite-element-method).

<a id="spt"></a>
## SPT correction

Liao, S. S. C., and Whitman, R. V. (1986). *Overburden Correction Factors for SPT
in Sand*. Journal of Geotechnical Engineering, 112(3), 373–377.
[Original article](https://doi.org/10.1061/(ASCE)0733-9410(1986)112:3(373)).
The square-root overburden relationship is identified separately from equipment
and energy normalization. For correction-factor practice, see GEER-049,
*Muisne, Ecuador Earthquake* report, section 6. The application requires measured
energy and adopted equipment factors, rather than inferring them from a hammer name.

<a id="ves"></a>
## Electrical sounding

U.S. Environmental Protection Agency. *Electrical Resistivity*, theory and
electrode geometry. The symmetric finite-spacing Schlumberger factor is stated
on the method card.
[EPA guidance](https://www.epa.gov/environmental-geophysics/electrical-resistivity).

<a id="pavement"></a>
## Rigid pavement

Florida Department of Transportation (July 2004), *Rigid Pavement Design Manual*,
document 625-010-006-c, figure 3.1: AASHTO 1993 rigid pavement equation, including
the coefficient 1.624×10⁷ used in the application.
[FDOT manual](https://fdotwww.blob.core.windows.net/sitefinity/docs/default-source/content/roadway/pm/publications/RPDM200407.pdf).
For parameter discussion, see FHWA NHI-05-037, chapter 6 and appendix C.
[FHWA reference](https://www.fhwa.dot.gov/engineering/geotech/pubs/05037/06a.cfm).
The original empirical kernel uses inches, psi and pci; SI conversions are explicit.

<a id="slopes"></a>
## Slope stability

Bishop (1955), Spencer (1967), Fellenius (1936), Janbu (1973), and Morgenstern
and Price (1965): the named limit-equilibrium methods. U.S. Army Corps of Engineers
(2003), *Slope Stability*, EM 1110-2-1902, discusses equilibrium and applicability.
The distributed numerical engine is XSLOPE 1.0.5; the BoreholeDesk adapter exposes
the variants stated in the slope chapter.
[XSLOPE method descriptions](https://xslope.org/en/latest/lem/overview/).

<a id="anchors"></a>
## Active tiebacks

FHWA (1999), *Ground Anchors and Anchored Systems*, GEC 4, FHWA-IF-99-015.
Caltrans (2024), *Ground Anchors and Soil Nails*, ground-anchor guidance.
[Caltrans guidance](https://dot.ca.gov/-/media/dot-media/programs/engineering/documents/geotechnical-services/202402-gm-groundanchorers-a11y.pdf).
The application uses adopted working loads, allowable capacities and explicit
free/bond geometry; those input decisions must be justified by the project.
