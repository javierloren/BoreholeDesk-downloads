# Calculation methods and data checks

## Rock Quality Designation (RQD)

Following Deere and Deere (1989), RQD is the percentage of the core run formed
by sound core pieces at least 100 mm long, measured along the core axis [1].
The metric definition is expressed as:

```math
\mathrm{RQD}\;(\%) = \frac{\sum_{i=1}^{n} L_i}{L}\times 100
```

- **Lᵢ**: length of each sound core piece with **Lᵢ ≥ 100 mm** (10 cm).
- **L**: total length of the core run being assessed, including unrecovered intervals.
- Use the same length unit in the numerator and denominator.

The inclusive 100 mm boundary and axial measurement are supported by Deere and
Deere [1] and the MnDOT manual, *Rock Quality Designation*, pp. 86–88 [2].
Distinguish natural discontinuities from identified drilling or handling breaks
when reviewing the core. These geological observations determine which pieces
are included; image segmentation supplies measurements for review.

### Worked example

For a 100 cm run with sound pieces of 60, 20, 10, 5 and 5 cm:

```math
\mathrm{RQD} = \frac{60+20+10}{100}\times100 = 90\%
```

This is an illustrative arithmetic example, not a reproduced field case.

## Core recovery

Core recovery is the recovered core length divided by the drilled run length,
expressed as a percentage [3, section 3.6.5.4]:

```math
\mathrm{Recovery}\;(\%) = \frac{L_r}{L}\times100
```

**Lᵣ** is the total recovered core length; **L** is the corresponding drilled run
length. Recovery and RQD are different quantities and are recorded separately.
For multiple runs, add the relevant lengths before calculating the percentage;
do not take an unweighted average of run percentages.

## Photographic scale and run information

Calibrate each photographed row using its measured physical length. A 60 cm row
is a calibration length, not automatically the length of a drilled run. Use the
depth blocks and drilling record to establish the run boundaries and core losses.
Review scale, piece boundaries and soundness before applying the calculated runs.

## Data checks

| Area | Checks and workflow |
| --- | --- |
| Borehole records | Depth ranges, overlapping intervals, run lengths and numeric consistency |
| Project files | Validated saves, previous-save recovery and save/reopen checks |
| Field sheets | Original and reviewed text, with explicit application of interpreted intervals |
| Core photographs | Physical calibration, depth blocks and reviewed measurements |
| Logs and reports | Saved project data feed log and report views |
| Installation | Component SHA-256 verification, selected-reader installation and repair |

## References

1. Deere, D. U., and Deere, D. W. (1989). *Rock Quality Designation (RQD) after
   Twenty Years*. Contract Report GL-89-1, U.S. Army Engineer Waterways Experiment
   Station. [Official NTIS record and abstract, ADA207597](https://ntrl.ntis.gov/NTRL/dashboard/searchResults/titleDetail/ADA207597.xhtml).
2. Minnesota Department of Transportation (2017). *Geotechnical Engineering Manual*,
   19 January 2017, *Rock Mass Characteristics*, pp. 86–88.
   [Manual](https://www.mndot.org/materials/manuals/geotechnical/geotechnicalmanual2017.pdf#page=86).
3. Federal Highway Administration (2006). *Soils and Foundations, Volume I*,
   FHWA NHI-06-088, section 3.6.5.4, p. 3-44.
   [Manual](https://www.fhwa.dot.gov/engineering/geotech/pubs/nhi06088.pdf).

Equations use metric notation for the cited definitions. The worked example and
explanations above are BoreholeDesk documentation; source publications are linked,
not reproduced. See the [User guide](USER_GUIDE.md) for operating instructions and
[Third-party notices](THIRD_PARTY_NOTICES.md) for software and model attributions.
