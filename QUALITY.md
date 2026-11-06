# Calculation methods and data checks

BoreholeDesk brings field records, core photographs, borehole data and reporting
into a local desktop workflow. The following methods and checks support that workflow.

## Rock Quality Designation (RQD)

RQD includes **sound core pieces greater than or equal to 10 cm in length**,
measured along the core axis.

**RQD (%) = 100 × total length of qualifying sound core pieces / drilled run length**

For example, four sound pieces of exactly 10 cm in a 60 cm drilled run give
**66.7% RQD**. A 100 cm run with sound pieces of 60, 20, 10, 5 and 5 cm gives **90% RQD**.

The physical row length establishes the photographic scale. The author's reference
boxes have **60 cm rows**; use the measured length for other boxes. Depth blocks
and run information define the drilled interval. Review piece boundaries and rock
classification before saving the calculated runs.

## Core recovery

**Recovery (%) = 100 × recovered core length / drilled run length**

When combining runs, results are weighted by their drilled lengths. Recovery and
RQD describe different properties and are recorded separately.

## Data and workflow checks

| Area | Built-in checks and workflow |
| --- | --- |
| Borehole records | Depth ranges, overlapping intervals, run lengths and numeric consistency |
| Project files | Validated saves, previous-save recovery and save/reopen checks |
| Field sheets | Original and reviewed text, with deliberate application of interpreted intervals |
| Core photographs | Physical calibration, depth blocks and reviewed measurements |
| Logs and reports | Applied project data feed the log and report views |
| Installation | Component SHA-256 verification, selected-reader installation and repair |

Review source readings, calibration, units and the selected calculation method
before applying results to a borehole or report. See the [User guide](USER_GUIDE.md)
for the complete workflow.
