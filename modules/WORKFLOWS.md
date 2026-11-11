# Field records, boreholes and reports

[Module index](../MODULES.md) · [User guide](../USER_GUIDE.md)

## Projects and boreholes

Create or open a local project, set its identification and coordinate reference,
and add boreholes. Enter lithology, log intervals, samples, water observations and
core runs in their respective editors. Use **Apply** before saving. Project
checks reject invalid depth ranges, overlapping intervals and inconsistent
numeric core-run values. Save the editable project outside the program folder;
PDF and HTML exports are outputs, not editable project backups.

The project preserves applied observations and cases. A changed save retains
one previous `.bak` revision. **File > Recover previous save** opens that revision
as an unsaved project for review and saving under a chosen name.

## Field sheets and OCR/handwriting

Import a supported scan, PDF or photograph in **Field sheets / OCR**. Choose a
printed-text or handwriting reader and the document language. Compare the
proposed text with the original and correct depths, units, sample identifiers
and descriptions. Use **Prepare intervals** to review structured intervals and
**Apply and preview** to add the reviewed data to the borehole.

The original, raw transcription and reviewed text have distinct roles. Ambiguous
punctuation stays literal until reviewed: `48-11` is not automatically `48.11 m`.
Reader proposals do not add geological intervals merely because recognition
has finished. Prepare the required local readers before working offline.

## Core photographs, recovery and RQD

Import a photograph, orient it and calibrate the actual physical ends of each
row. A measured 60 cm row establishes image scale; it does not automatically
establish the drilled interval. Review sound/fractured regions and individual
piece boundaries, identify depth blocks and reconcile the drilling record.
Calculate the reviewed runs and explicitly save them to the borehole.

RQD includes sound pieces **at least 10 cm** long measured along the core axis.
Recovery and RQD have different numerators and use the corresponding drilled
run length. See the [RQD and recovery reference](../QUALITY.md) for equations
and primary sources. Source observations and interpreted/calculated results
should remain distinguishable in the record.

## Stratigraphic logs and original columns

Review **Log intervals** and the borehole log preview. Interval boundaries,
material descriptions, samples, SPT, recovery, RQD and water observations feed
the log from applied project data. Original drawn columns can be retained as
depth-aligned source material. Displayed contacts and patterns must reflect the
reviewed observations and interpretation. Check output scale and pagination
before printing or sharing.

## Geological sections

Use **Depth comparison** to compare borehole columns by depth, or **Spatial
section** when coordinates and elevations establish their spatial relation.
Review ordering, contacts and vertical datum; save the interpreted section and
export it to PDF. A drawn contact is an interpretation, not an automatically
verified geological boundary. Ground sections can supply slope geometry with
source provenance; material strength and groundwater remain engineering inputs.

**Digitize scanned section** calibrates an image/PDF to known station/elevation
references and adds manually picked contacts for review. **Source image** displays
the calibrated preview retained in the project. **Interpreted units** fills the
common extent between named upper/lower contacts with a user-selected color and
pattern; crossed limits and overlapping units are rejected. Source-image and
unit visibility settings are saved and used by PDF/SVG and complete reports.
See the [section workflow](../GEOLOGICAL_SECTIONS.md).

## Site plan and location exchange

**File > Import investigation locations** reads supported collar/location tables
and geospatial records. Review the column mapping, location IDs, coordinate
reference, elevations and final depths before applying them. Supported location
readers include CSV, Excel, KML/KMZ and GeoJSON. Exports include collar CSV,
site-plan SVG, KML and GeoJSON. These are location-exchange workflows, not a claim
that an entire borehole record is exchanged through every listed format.

KML uses geographic longitude/latitude conventions. Do not label local metres as
geographic coordinates or assume a datum transformation has occurred merely
because a file has been imported.

## Samples and campaign data checks

**Tools > Sample register** provides a project-level view of sample records.
**Tools > Campaign quality** brings together checks for inconsistent depths,
identifiers and project data requiring review. Resolve flagged records against
their source evidence. A data-consistency check does not determine a soil's
strength or the representativeness of a sample.

## Calculation worksheets

The [calculation catalogue](../MODULES.md) documents every worksheet exposed in
**Computation**. A case stores selected methods and inputs; calculation produces
the schedules, graphs and outputs for review. Record the basis of adopted
parameters and factors. Recalculate after changing a case and inspect numerical
warnings before exporting its calculation report.

## Reports and exports

Use **Report setup** and the preview to select the required content, then export
PDF or HTML. Review borehole identifiers, source readings, intervals, units,
descriptions, interpretation and page boundaries. Specialist calculations have
their own input schedules, method notes and calculation reports.

Keep project files and source material with your own backups. Review the
contents of every report before sharing confidential field information.

## Technical dictionary and support

The installed technical glossary supports English/Spanish term lookup alongside
the workflow; it is not a design-code selector. **Help > Export diagnostic
report** prepares a local version/reproduction report for review before sharing.
It is not sent automatically. Use a minimal reproduction and exclude private
documents, credentials and personal information from issue attachments.
