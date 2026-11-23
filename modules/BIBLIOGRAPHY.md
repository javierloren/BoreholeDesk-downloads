# Technical bibliography

[Module index](../MODULES.md)

<a id="spanish_foundation_guidance"></a>
## Spanish foundation design guidance

Ministerio de Fomento / Dirección General de Carreteras (2019), *Guía para el
proyecto de cimentaciones en obras de carretera con Eurocódigo 7: Cimentaciones
superficiales*. Distinguishes actions, characteristic/design values, ultimate
limit states and serviceability checks. The guide acknowledges technical review
by Carlos Oteo Mazo and Antonio Soriano Peña among its contributors.
[Official guide](https://cdn.transportes.gob.es/portal-web-transportes/carreteras/normativa_tecnica/08.1_guias_tecnicas/guia_proyecto_cimentaciones_con_eurocodigo_7_cimentacione_superficiales.pdf).

The introductory notice in the official file of the older *Guía de cimentaciones
en obras de carretera* distinguishes its global-factor approach from the
Eurocode basis required for specified State road works under OC 1/2019.
Keep the adopted project rules separate from individual analytical methods;
do not relabel a global-factor calculation as a complete Eurocode verification.
[Official legacy guide and notice](https://cdn.transportes.gob.es/portal-web-transportes/carreteras/normativa_tecnica/08_geologia_geotecnia/0710401.pdf).

<a id="consolidation_time"></a>
## Time rate of primary consolidation

Terzaghi's one-dimensional consolidation solution for uniform initial excess
pore pressure and specified drainage boundaries. J. Atkinson, *GeotechniCAL*,
Consolidation: mathematical model, Terzaghi's solution and drainage path length.
[University-hosted reference](https://environment.uwe.ac.uk/geocal/soilmech/consol/soilcons.htm).
Illinois DOT (2020), *Geotechnical Manual*, Appendix D.9.3, settlement-time
estimation, equation D.9.3-1: t = Tv Hdr²/cv; rounded Tv50 = 0.197 and
Tv90 = 0.848. The program solves the series rather than adopting these rounded
time factors. [Manual](https://idot.illinois.gov/content/dam/soi/en/web/idot/documents/doing-business/manuals-guides-and-handbooks/highways/materials/geotechnical-manual.pdf).

<a id="secondary_compression"></a>
## Secondary compression

USACE (1990), *Settlement Analysis*, EM 1110-1-1904, section 3-18,
equation 3-30 and example on printed page 3-54. The reference-state void ratio
converts Cα, expressed as change in void ratio per log10 time, into strain.
[Manual](https://www.publications.usace.army.mil/Portals/76/Publications/EngineerManuals/EM_1110-1-1904.pdf).

<a id="service_movements"></a>
## Foundation service movements

Ministerio de Fomento (2019), *CTE DB SE-C Cimientos*, section 2.4.3, Figure 2.1
and equations 2.6-2.7 (printed p. SE-C-9). Defines differential settlement,
angular distortion and relative rotation. Select the project service criterion
for the actual structure and adopted design basis; the worksheet does not
automatically assign the limits in Table 2.2.
[Official document](https://www.codigotecnico.org/pdf/Documentos/SE/DBSE-C.pdf).

<a id="seismic_moduli"></a>
## Elastic wave velocities and dynamic moduli

US EPA, *Environmental Geophysics: Acoustic Logging*, equations 3-5, and
*Seismic Velocities (Vs, Vp)*, equation 1, after Wightman et al. (2003),
FHWA-IF-04-021. Isotropic elastic wave relations with representative bulk mass
density; no automatic dynamic-to-static modulus conversion.
[Acoustic logging](https://archive.epa.gov/esd/archive-geophysics/web/html/acoustic_logging.html),
[seismic velocities](https://archive.epa.gov/esd/archive-geophysics/web/html/seismic_velocities.html).

Method cards identify the specific formulation and application conditions used
by BoreholeDesk. The references below establish the scientific or engineering
basis. Citations identify the formulation and its application conditions.
Equations are presented in the notation used to explain the implementation.
Original books, figures, graphical charts and private workbooks are not reproduced.

<a id="pile_cyclic"></a>
## Axial cyclic pile loading

Puertos del Estado (2005). *ROM 0.5-05, Recomendaciones Geotécnicas para Obras
Marítimas y Portuarias*. Section 3.6.3.5, printed pp. 238-241 and Figure 3.6.6
(radial safety-factor construction); section 3.6.4.1, p. 242 (compression head
equilibrium); section 3.6.7.1, p. 263 (uplift resistance).
[Publisher's document](https://www.puertos.es/system/files/2024-04/ROM%200.5-05.pdf).
The formulas and independently drawn interaction plot describe a stationary
axial resistance envelope; they do not constitute a fatigue-life model or
automatic Eurocode verification.

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

U.S. Army Corps of Engineers (1990). *Settlement Analysis*, EM 1110-1-1904:
stress-distribution and vertical-strain framework. BoreholeDesk integrates rectangular-load stress increments through
independent layers with supplied constrained moduli and a fixed-bottom condition.
[USACE manual](https://www.publications.usace.army.mil/Portals/76/Publications/EngineerManuals/EM_1110-1-1904.pdf).

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

Goodman, R. E., and Shi, G.-H. (1985). *Block Theory and Its Application to Rock Engineering*. Prentice-Hall.
Goodman, R. E. (1995). *Block Theory and Its Application*, 35th U.S. Symposium on Rock Mechanics, ARMA-95-0003.
[Author's paper](https://onepetro.org/ARMAUSRMS/proceedings-abstract/ARMA95/ARMA95/ARMA-95-0003/130565).
BoreholeDesk accepts an explicit tetrahedron and evaluates its geometry and a
strict gravity-release condition. Automatic block searches and equilibrium analysis are outside this method's scope.

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
Classification and Support Design*. Sections 2.4 (Qbase, printed p. 8),
3.1-3.2 (Q equation, parameter selection and RQD minimum convention) and
4.1 (equivalent dimension).
[NGI handbook](https://www.ngi.no/globalassets/bilder/forskning-og-radgivning/bygg-og-anlegg/q-handbook_2025_english_final.pdf).

<a id="european_french"></a>
## European design basis and French photovoltaic foundations

European Commission JRC, [national implementation of Eurocodes](https://eurocodes.jrc.ec.europa.eu/en-eurocodes-implementation/national-standards)
and [second-generation transition](https://eurocodes.jrc.ec.europa.eu/second-generation-eurocodes).
Adopt the project edition and its National Annex together; the family-wide
publication deadline is 30 September 2027 and withdrawal deadline is 30 March
2028. National adoption and the contract determine the applicable project basis.

AFNOR, [Eurocodes framework](https://normalisation.afnor.org/thematiques/eurocodes/):
EN 1990 basis, EN 1991 actions, EN 1997 geotechnical design, relevant EN 1993
steel parts and National Annexes. For steel piles see
[NF EN 1993-5](https://www.boutique.afnor.org/fr-fr/norme/nf-en-19935/eurocode-3-calcul-des-structures-en-acier-partie-5-pieux-et-palplanches/fa119785/29662)
and its French National Annex. Check the appropriate provisions for cold-formed sections.

Cerema, *Eurocode 7 - Application to deep foundations (NF P94-262)*,
[application guide](https://doc.cerema.fr/default/digitalCollection/DigitalCollectionAttachmentDownloadHandler.ashx?documentId=583651&parentDocumentId=14121&skipCopyright=true&skipWatermark=true).
AFNOR [NF P94-151](https://norminfo.afnor.org/consultation/nf-p94-151/sols-reconnaissance-et-essais-essai-statique-de-pieu-isole-sous-effort-transversal/128489)
concerns static lateral pile loading; [NF EN ISO 22477-2:2023](https://www.boutique.afnor.org/fr-fr/norme/nf-en-iso-224772/reconnaissance-et-essais-geotechniques-essais-des-structures-geotechniques-/fa199993/350658)
concerns static axial tension loading and replaces NF P94-150-2. Do not use the
axial test procedure as a lateral calibration rule.

These references identify the design/test framework; they do not establish a
universal displacement limit or turn a named empirical calculation into a
complete code verification. Adopt serviceability criteria for the supported
structure and the project specification.

<a id="beam"></a>
## Lateral beam and subgrade reaction

Caltrans, *Effects of Soil Slope on Lateral Capacity of Piles*, section 2.1,
equations 2.1–2.2: beam/soil interaction framework.
[Caltrans report](https://dot.ca.gov/-/media/dot-media/programs/research-innovation-system-information/documents/f0016560-final-report-task-0932.pdf).
The BoreholeDesk card states its linear Euler–Bernoulli/Winkler model,
depth distributions and test-based calibration explicitly.

MIT OpenCourseWare, *Solid Mechanics*, 1.050 (2004), chapter 10,
*Deflections due to Bending*: curvature integration and superposition of beam
flexure with support rotation.
[Lecture chapter](https://ocw.mit.edu/courses/1-050-solid-mechanics-fall-2004/f9a4d5764b9b0f51ffaacbdf69f7aed8_emech10_04.pdf).

FHWA (2018), *Design, Analysis, and Testing of Laterally Loaded Deep Foundations*,
GEC 9, FHWA-HIF-18-031: lateral load testing, soil-structure interaction and
nonlinear p-y analysis. A calibrated linear Winkler response does not establish
axial uplift capacity or ultimate lateral resistance.
[FHWA manual](https://www.fhwa.dot.gov/engineering/geotech/pubs/hif18031.pdf).

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
Zhu, D. Y., Lee, C. F., Qian, Q. H. and Chen, G. R. (2005), *A concise algorithm for computing the factor of safety using the Morgenstern-Price method*, Canadian Geotechnical Journal 42, 272-278, equations 1 and 7 (force and moment equilibrium). [Publication](https://doi.org/10.1139/t04-072).
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


<a id="geophysical"></a>
## Measured geophysics and least squares

Keys, W. S. (1990), *Borehole Geophysics Applied to Ground-Water Investigations*,
USGS Techniques of Water-Resources Investigations, book 2, chapter E2.
[USGS publication](https://pubs.usgs.gov/publication/twri02E2).

U.S. Environmental Protection Agency, *Borehole Self-Potential*: measurement,
fluid chemistry, lithology and interpretation.
[EPA guidance](https://www.epa.gov/environmental-geophysics/borehole-self-potential).

NIST/SEMATECH, *e-Handbook of Statistical Methods*, sections 4.1.4.1 and 4.4.3.1,
linear least squares and residual assessment.
[Least squares](https://www.itl.nist.gov/div898/handbook/pmd/section1/pmd141.htm),
[Model assessment](https://www.itl.nist.gov/div898/handbook/pmd/section4/pmd431.htm).


<a id="rock_modulus"></a>
## Rock-mass deformation modulus

Hoek, E. and Diederichs, M. S. (2006), *Empirical estimation of rock mass modulus*,
International Journal of Rock Mechanics and Mining Sciences, 43(2), 203-215.
Equations 2 (simplified) and 4 (with intact modulus); effectively isotropic rock
masses. [Original publication](https://doi.org/10.1016/j.ijrmms.2005.06.005).


<a id="hoek_brown"></a>
## Generalized Hoek-Brown strength

Hoek, E., Carranza-Torres, C. and Corkum, B. (2002), *Hoek-Brown failure criterion -
2002 edition*, NARMS-TAC, 1, 267-273, equations 2-10 and 12-13.
[Original paper](https://www.rocscience.com/assets/resources/learning/hoek/2002-Hoek-Brown-Failure-Criterion.pdf).

Hoek, E. and Brown, E. T. (2019), *The Hoek-Brown failure criterion and GSI -
2018 edition*, JRMGE 11(3), 445-463, especially geological scale, confinement and
limits of applicability. [Publication](https://doi.org/10.1016/j.jrmge.2018.08.001).

<a id="barton_joint"></a>
## Joint peak shear strength and scale

Barton, N. and Choubey, V. (1977), *The shear strength of rock joints in theory
and practice*, Rock Mechanics 10, 1-54.
[Publication](https://doi.org/10.1007/BF01261801).

Barton, N. (2013), *Shear strength criteria for rock, rock joints, rockfill and
rock masses: Problems and some solutions*, JRMGE 5(4), 249-261.
[Publication](https://doi.org/10.1016/j.jrmge.2013.05.008).
Peak joint strength, residual friction and empirical JRC/JCS scaling; no assumed
cohesion for matching unfilled joints.


<a id="calculix"></a>
## Local plane-strain FEM engine

Dhondt, G. and Wittig, K., *CalculiX CrunchiX 2.23 User's Manual* (2025),
CPE3 plane-strain elements, elastic materials, static analysis and printed
nodal/element output. [Author's manual](https://www.dhondt.de/ccx_2.23.pdf).
The elastic worksheet uses one metre out of plane, consistent strip loads
and tension-positive stresses. CalculiX is obtained unmodified from its author;
its general solver capabilities do not expand the worksheet's stated model.

<a id="pile_hyperbolic"></a>
## Hyperbolic lateral pile response

Stuedlein, A. W. and Li, Q. (2018), *Effects of High Strength Steel Bars and
Steel Casing on the Response of Drilled Shafts*, ODOT SPR 765 /
FHWA-OR-RD-18-09, section 2.5.11, p. 47, equation 2.92.
[ODOT report](https://www.oregon.gov/odot/Programs/ResearchDocuments/SPR765_Drilled_Shafts_Response.pdf).
The worksheet uses the monotonic hyperbolic p-y relation with supplied
site-specific parameters and an elastic Euler-Bernoulli beam.

<a id="rom_piles"></a>
## Pile group load distribution, negative friction, settlement and lateral soil failure

Puertos del Estado (2005), *ROM 0.5-05*. Section 3.6.10.1, printed p. 273 (axial spring framework for load distribution); section 3.6.3.4.1, pp. 232-234 and Figure 3.6.3 (negative friction and settlement compatibility); section 3.6.9.1.1, p. 269 (simplified individual settlement); section 3.6.8.1, pp. 265-267 and Figure 3.6.12, and section 3.6.8.3, p. 268 (general rigid-pile lateral GEO model).

[Publisher document](https://www.puertos.es/system/files/2024-04/ROM%200.5-05.pdf). These geotechnical methods retain their stated assumptions; they do not establish a complete Eurocode structural or jurisdictional verification.
