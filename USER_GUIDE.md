# BoreholeDesk User Guide

BoreholeDesk is a desktop application for geological and geotechnical field
records, borehole logs, core photographs, interpretation and reports. This guide
describes **BoreholeDesk for Windows x64**. Public user documentation
is maintained in English; source documents may be in English or Spanish.

## 1. Download and install

1. Open the [official BoreholeDesk download page](https://github.com/javierloren/BoreholeDesk-downloads)
   and follow its **Download for Windows** link.
2. In **Assets**, choose the installer ending in **Complete-Windows-x64.exe**
   if you want to work with handwritten field sheets from the start.
   Choose **Quick-Windows-x64.exe** for printed OCR and the core tools.
   GitHub's **Source code** archives are for source access.
3. Run the installer. It installs for your current Windows user without requiring
   administrator rights, a separate Python installation or an online account.
4. The installer preselects the choice named in your download. Follow its progress.
   It obtains and verifies the selected components automatically.
5. Open BoreholeDesk from the Start menu. Choose **File > Open example project**
   to explore fictitious data, or create a project of your own.

Workspace headings identify the current task. Use **Ctrl+K** to find another task
or calculation by name. **View > Focus workspace** (**F11**) temporarily hides
the side panels to give tables and diagrams more room; F11 restores their previous
visibility without discarding editor drafts. Ctrl+K leaves focus view and opens
task search. **View > Restore side panels** restores the standard arrangement.

| Installation | Total download, including the installer | Local readers |
| --- | --- | --- |
| Quick trial | Approximately 0.79 GB | Printed/scanned OCR, photographic RQD, local FEM and the slope engine are included; handwriting readers can be added later |
| Complete | Approximately 4.67 GB | All selected handwriting and whole-column readers are prepared for offline use |

Both EXEs are small initial installers; the total download depends on the selected edition. Both choices use
the same models and algorithms. The Quick edition can be expanded later without changing its models.
Handwriting readers add approximately 1.95 GB; the advanced whole-column reader
adds approximately 1.93 GB. Selecting a missing reader offers a one-time guided
installation. **Help > Install local readers** installs the remaining readers.
After installation finishes, press **Read page(s)** again; your project stays open.

### Offline installation

For a prepared offline installation, download the
[matching component list](https://github.com/javierloren/BoreholeDesk-downloads/releases/download/v0.1.3-components/downloads.json).
Its `packages` entries give the ten filenames and public download links used by
these installers. Put those files in a **Packages** folder beside the EXE, then
run the installer. Keep filenames intact and use the matching list; the installer
verifies and restores the files itself.
Also put the unmodified [CalculiX 2.23 Windows archive](https://www.dhondt.de/calculix_2.23_4win.zip)
in that folder as `calculix_2.23_4win.zip`. The installer verifies it and retains
only the local FEM solver. If it is absent, the installer obtains it from the
author's website. Calculations run offline after installation.
Install all readers you will need before going to a site without internet access.
Keep the installer and matching packages if you want to repair the installation offline.

Windows 10/11 x64 is the target platform. For the complete edition, 16 GB of RAM
and 25 GB of free disk space are recommended for downloading, installing and
retaining the package. A GPU is not required. First use of a model can take longer
while its weights load into memory.

### Download checks

Check the publisher shown by Windows and the SHA-256 published with the download.
Keep system protection enabled. If Windows blocks the installer, report the
installer name, version and warning to the download maintainer.
SHA-256 detects changed files; it does not establish publisher identity or certify
engineering results. Obtain the installer from the official release page and keep
it with its matching component assets when preparing for offline installation.

### Workspace navigation

Use **Find task or method...** above the Tasks panel, or press **Ctrl+K**, to
search tasks and all calculation methods by name, family or purpose. Press
**Enter** to open a match, or select a specific result in the tree. Calculation
matches appear during a search; clearing it returns to the compact task list.
Searching leaves the current editor and its drafts open. Clear the search to
show every task; choosing a hidden destination through a menu reveals it.
Opening a different calculation method keeps the existing save/discard check
when it would replace an edited case.
**View > Restore side panels** returns the Project explorer and Tasks panels
to their usual positions without changing project data or editor drafts.

Every calculation displays its purpose before the inputs. The Input guide links
take you directly to each input tab. Its graph is labelled as an illustrative
example; calculate to obtain results from your own entries. Other workspaces
show a short workflow above their controls.

In calculation tables, **Tab** and **Shift+Tab** move between visible editable
cells, skipping labels and calculated values. Paste only into visible inputs;
a rejected paste leaves the table unchanged. **Calculate**, or **F5** while the
calculation workspace is active, takes you to a missing or malformed numeric
input when its location is identifiable. Automatic recalculation shows errors
without moving you away from the cell you are editing.

Use **Expand inputs** when entering long tables or working in a small window.
Press **F5** to calculate: a successful explicit calculation restores the split
workspace and shows the actual Results tab. **Expand results** enlarges the
output panel; either option can be turned off to return to the split layout.

Calculation tabs use short labels such as **Input guide**, **Schedule** and
**References**. Hover over a shortened label for its full title. Input tables,
method references and calculation results keep their existing roles.

### Pile ground profiles and preliminary alternatives

In a layered pile worksheet, open **Layers > Ground profile...** to edit one
layer at a time with labelled fields and a depth preview. **Add layer** copies
only the previous bottom into the new top; it supplies no soil properties.
The preview shows the selected layer, pile toe and groundwater from your inputs.
For axial load-transfer methods, the last layer bottom defines the toe. In the
diameter/length comparison, enter pile geometries in **Cases**. The drawing
uses schematic pile width; layer depths are plotted to a common vertical scale.

**Apply ground profile** transfers the draft layers to the worksheet. **Cancel**
leaves the worksheet unchanged. Review adjoining depths and local cell formulas
after deleting a layer. Choose **Layers** or **Nodes** where both are offered;
the layer editor does not replace a nodal profile automatically.

In **Piles > Sand - diameter / length design table**, optional head compression
and uplift demands add resistance-minus-demand margins. Enter loads on the same
allowable-load basis as the calculated resistances. Uplift comparison requires
the pile unit weight, uplift shaft ratio and safety factor. The shortest passing
length is selected only among the circular-pile alternatives you entered and
only for the axial demands supplied. It is not an interpolated design or a
structural, lateral or cyclic verification. Use the calibrated lateral profile
test worksheet separately for lateral displacement checks.

For axial cyclic loading, choose **Piles > Pile cyclic axial loading - ROM 0.5-05**.
Enter unfactored static shaft and toe resistances, effective embedded pile weight
and the project-adopted radial safety factor in **Parameters**. In **Cycles**,
enter each signed minimum/maximum head load: compression positive, uplift
negative. Calculate to review factors and the interaction diagram; save the case
and export its PDF as with other worksheets. The method assumes many axial
cycles; it does not predict fatigue life, accumulated movements or lateral
hysteresis. See [the method reference](modules/PILES.md#pile_cyclic).

The **Piles** family also includes:

- **Rigid pile cap**: enter cap N/Mx/My and pile X/Y coordinates with adopted
  axial group stiffnesses. The solver distributes vertical reactions, including
  uplift when present. It does not solve lateral cap loading or cap bending.
- **Negative skin friction**: enter mobilized shaft drag stresses and either an
  adopted neutral depth or reviewed trial settlement-compatibility curves. The
  entered curves must include the trial drag-zone load and remaining support.
- **ROM service settlement**: enter nominal head resistance, material area,
  equivalent diameter, elastic modulus, free/embedded lengths and transfer alpha.
  Results include individual settlement and an equivalent axial spring stiffness.
- **ROM lateral soil failure**: enter the short rigid-pile geometry, equivalent
  horizontal load height, contact-loss depth and layered limiting-pressure inputs.
  Soil resistance does not replace a separate pile-section check.

These methods retain the assumptions and factor conventions in the
[pile method reference](modules/PILES.md). Adopted limits and resistance factors
are project inputs; a reference entry is not an automatic design-code check.

## 2. Create, edit and save a project

1. Create a project or open the synthetic example. Save it under a name of your own.
2. Add a borehole from **Data > Add borehole** and enter the investigation details.
3. Enter or import your observations. Use each editor's **Apply** action before
   saving. Unapplied drafts are not included in the saved project or report.
4. Review **Log intervals**, **Core runs / recovery / RQD** and **Report preview**.
5. Save the `.boreholedesk.json` project outside the program folder, for example
   in your Documents folder. Export PDF or HTML only after reviewing the data.

Overlaps, invalid depths and physically inconsistent numeric core-run data are
rejected. A rejected edit must be corrected; it is not silently repaired.
In the core-run table, calculated run length and recovery columns are read-only.
Use **Apply table** to validate and store edits. RQD is entered or reviewed
separately; it is not inferred from recovery percentage.

Keep your original field documents, photographs and external project backups.
A project can preserve page images and annotations, but do not assume it replaces
your complete original PDF or your own document archive.

## 3. Read and review a field sheet

### Import or export campaign tables

**File > Import campaign tables…** accepts CSV, TSV and XLSX files for locations,
geology intervals, field records and core runs. Select each sheet and map its
columns. Choose the depth/elevation unit, numeric decimal convention and source
CRS explicitly; X/Y coordinates follow the CRS units. Read the proposed additions
and updates before applying them. Replacing populated values requires the update
option; omitted populated columns or sheets require acknowledgment. An invalid
batch leaves the project unchanged.

**File > Save blank campaign template…** creates the four-sheet XLSX template.
**File > Export campaign workbook…** exports the same structure and assigns stable
field-record/sample identities where needed. Save the project after exporting to
retain those identities, and keep their columns intact when editing the workbook.
Sample labels alone are not unique identities. This exchange does not transfer
source attachments, page links, photograph annotations or approvals; keep the
`.boreholedesk.json` project as the editable backup. Ambiguous observation text
remains literal. Spreadsheet formulas must be replaced with reviewed values
in a copy before import.

### Read a scanned page

1. Use an empty borehole when testing a sheet that would overlap existing intervals.
2. In **Field sheets / OCR**, import a supported PDF or image.
3. Choose **Printed text (RapidOCR)** for printed text or a handwriting reader for
   handwritten material. Select the appropriate document language.
4. Press **Read page(s)**. If a model is missing, accept its installation or
   cancel and continue with manual entry. Python setup is not required.
5. Compare the proposed transcription with the original, especially depths,
   sample identifiers, decimal separators, units and crossed-out notes.
6. Correct the text, then use **Prepare intervals** and **Apply and preview**
   only after reviewing the proposed structured data.
7. In the report preview, check the intervals against the original. Choose
   **Export PDF...** to save the report, and save the project to keep the source
   document and reviewed data together.

### Mark and review uncertain handwriting

When its optional local model is installed, **Selected handwritten line - direct
characters** offers a fast alternative that decodes image characters without a
dictionary or sentence completion. It still makes recognition errors and does
not certify words or depths. Select exactly one handwritten line and enable
**Read selected region only** before reading. For field-table rows, each selected
source row must contain one text line; use a whole-column or cursive reader for
multiline descriptions. Compare it with the whole-column or cursive reader
against the source, using **Compare previous reading...** to retain the clearer
draft. On bright blue-ruled paper, this reader reduces the pale background in
its reading copy. The original is preserved. No extra model is downloaded automatically
by this reader; the option appears only when its model/runtime are available.

**Handwriting - conservative two-pass reading** compares a general reading with
a lighting-corrected reading, using the Spanish cursive variant when Spanish is
selected. Disputed tokens become **[illegible]** rather than choosing a proposed
word. It takes longer and may leave readable words unresolved. Agreement is a
stability check, not a calibrated confidence or proof of correctness; inspect
the remaining text against the source too.

The pale background identifies an editable draft, including words without a
marker. **Whole-column handwriting** also replaces weak token readings with
**[illegible]** instead of completing a word or number. This check may leave
readable words unresolved. A high model score is not proof that a word is correct;
compare the remaining text with the source too.
This reader recognizes the source automatically. Its language selector is
disabled; switch to a line reader to select a language-specific pack.

Marked gaps have an amber background in the transcription and interval
preview. **Next marked gap** selects the next marker and shows its source page
when available. Replace it only after reading the original, or use **Mark
selection unreadable** to insert a marker yourself. The literal marker survives
plain-text saving, project reopening and the report; colour is not the only
indicator. A marker denotes an unresolved fragment, not a known count of words.
An interrupted reading is labelled **Partial reading**. Its partial-transcription
marker is highlighted in amber and can be selected with **Next marked gap**.
Read a smaller source region to recover the remainder; the application does not
complete it from context.

**Straighten ruled reading image** is an optional reading setting. It estimates
a small rotation only when several long, separated ruling lines can be aligned.
The original and all its ink are retained; only a reading copy is rotated. This
does not correct perspective or curved pages. Leave it off for an unchanged
baseline and compare transcriptions before choosing a result. It does not infer
depths or guarantee a more accurate reading.

Use **Reading settings** to fold or unfold the existing reader, language, page,
rotation and reading-region controls. Folding keeps every setting and leaves a
summary visible. After a complete, nonempty reading the controls fold to give the
original and transcription more room. Expand them again to retry or change a
setting. Empty or partial readings keep the controls open. The Original selector
remains available in either view.

Use **Prepare intervals...**, review the explicit depths and descriptions, check
the source-review box, then choose **Apply and preview**. The text becomes the
description in the borehole log without copying it again. Marked gaps remain
visible in the report until corrected; no material or colour is inferred from
a description containing them. Editing an interval clears the review checkbox.
The highlighted **Prepare intervals...** action opens the interval editor;
**Apply and preview** becomes available after you check the source-review box.
Moving between tasks does not apply or discard an interval draft.

Double-click a proposed interval in the transcription preview to display its
original page. In **Log intervals**, select a row and choose **View original**
to return to its attached document and source page without discarding interval
edits. Clicking within a page-labelled transcription also displays that page.
These actions locate the page, not the exact handwritten word on the image.

Preparing the same transcription again does not duplicate identical applied
intervals. Changed proposals at the same depths, source and page require explicit
replacement confirmation; other applied intervals are kept. Different depth
ranges remain subject to the usual overlap checks. Review and apply the prepared
table before the changes appear in the report.

Report preview shows the counts of applied lithology intervals, field
observations, core runs and marked gaps in log descriptions. These counts describe
the applied data; they are not a completeness or OCR-accuracy score. Unapplied
drafts remain excluded from export and are identified in the preview notice.
Unreadable depths must be checked against verified source information. They are
not repaired from isolated OCR numbers. In table/row reading, confirmed depths
remain separate from the handwritten description.

### Read a table with depths and descriptions in separate columns

Use **Read field table rows...** instead of reading the entire grid as a paragraph.
Choose the handwriting reader and use **Add source row...** to select each
description on the original. Enter that row's From/To depths as written. **Find
ruled rows...** can propose regions from the body of a description column;
inspect each region, correct or remove proposals and add any missed rows. A
printed ruling line does not necessarily mark a geological boundary.

Optionally enter the known depths at the first and last detected rule. This
explicit calibration proposes intermediate depths using a linear source scale;
it does not read the numbers or establish geological boundaries. Check every
proposal, especially on distorted photographs or sheets with a nonlinear scale.
Leave both calibration values blank to enter each row's depths manually.
Calibrated depth proposals are amber. Confirm the source boundaries and depths
before reading; changing a depth or source region clears this confirmation.
Ambiguous values such as `48-11` require checking the original before entering
a numeric depth; they are not converted to decimals automatically.

Choose **Read selected rows** to read each region separately. The resulting
draft preserves the entered range beside its description. Correct readings,
then use **Prepare intervals** to review and apply them. Original page numbers
and source documents remain attached. Neither a successful reading nor a
detected grid constitutes approval of the handwritten text.
An unreadable source row keeps its confirmed depth range and an `[illegible]`
marker, so that a missing description does not erase the row structure.
Marked gaps appear in amber in the log sheet and PDF descriptions. To reproduce
drawn symbols, select and depth-align the **Original geology column**; this
preserves the original drawing rather than classifying it from OCR text.
From field reading, **Preview report** shows a read-only draft schematic when
depth intervals have been proposed but not applied. **Review intervals** opens
the editable interval table; closing the draft does not change the project.
An empty report also offers **Review field data** to return to
the relevant editor. Confirm the intervals and choose **Apply and preview**.

For a handwritten column of numbers, try **Whole-column handwriting** and select
only that column, keeping leading digits and decimal marks inside the selection.
For Spanish cursive descriptions, choose **Cursive text** with **Spanish**.
For unevenly lit photographs, try **Photographed handwriting - lighting correction**.
It adjusts paper illumination for recognition and keeps the source unchanged.
Use **Compare previous reading...** to compare the previous and current text in
the same session, then keep the clearer reading and correct it against the source.
When both readings cover the same page range, region and rotation, with matching
line breaks, **Use text with marked gaps** offers a third preview. It retains
exact word agreements and replaces differences with amber **[illegible]** markers.
Lines remain separate so a depth or description is not matched to another row.
For differently wrapped or long readings, select a single line for comparison.
Agreement is not a confidence score: both readers can make the same error or
omit text. Selecting this preview changes only the unapproved draft; check the
original before preparing and applying intervals.
Lighting correction can help some words and worsen others.
The reader rejects detectable corrupt characters and repetitive generation;
these checks do not establish that the remaining words match the handwriting.
Compare every proposed reading with the source before including it in a report.
When selecting a single text line, include its complete accents and punctuation.
Rotate sideways or upside-down sheets with the OCR rotation control before reading.
If a photograph contains shadows, folds or crossed-out values, compare the draft
with the original; no reader approval replaces this review. Covered or redacted
parts of a document must not be reconstructed from context.

A depth description can be written as `5.00-5.40: Light brown clayey sand`.
Ambiguous writing must remain literal until reviewed: for example, **48-11**
must not automatically be interpreted as **48.11 m**. If no intervals are
recognized, review the transcription; do not assume report data were added.

Review the proposed text before adding it to a borehole or report. Reader confidence
helps prioritize review; approval of the depth, units and geological meaning comes
from comparison with the original field record.

**Save text draft** keeps the editable transcription in the project. The report
includes saved transcriptions grouped by source document and page, together with
the original records when that annex is selected. Only intervals explicitly
reviewed and applied populate the lithology table and geological column. Saving
a transcription does not turn isolated numbers into depth intervals.

## 4. Core photographs, recovery and RQD

### Manual reference example

In **Image RQD > Calculate manual RQD**, use a 100 cm drilled run and pieces of
60, 20, 10, 5 and 5 cm. Expected RQD is **90%**. RQD includes sound core pieces
**at least 10 cm long**, measured along the core axis (Deere and Deere, 1989). Four pieces of exactly 10 cm in a 60 cm drilled run give
**66.7%**. Recovery and RQD use the drilled run as their denominator;
combined results must be weighted by run length rather than averaging percentages.

### Photographic workflow

1. Choose **Local model (offline, trial)** and load a core-box photograph.
2. Calibrate the two physical ends of each visible row using a measured length.
   For a measured **60 cm row**, enter 60 cm. Measure each box; do not
   stretch the visible rock extent to fill the row.
3. Mark and fix the depth blocks, then run **Process segmentation**.
4. Review solid/fractured regions, individual pieces, row assignments, scale,
   depth blocks and the actual drilled interval. Correct mistakes before calculating.
5. Calculate the reviewed intervals and explicitly save the runs to the borehole.
   Reopen the saved project and check the reported values.

Depth blocks remain part of the workflow. The apparent length of rock in a
photograph does not establish drilled run length or missing core. Fracture
interpretation and treatment of drilling-induced breaks require professional
judgment.

## 5. Logs, geological sections and reports

The task navigator follows four stages: **1. Field data**, **2. Ground model**,
**3. Engineering**, **4. Reports**. Start with a scanned field record or enter
intervals and drilling/sample records manually. Review OCR text against the
original; prepare and apply approved intervals. Enter SPT blows and penetration
increments as recorded in **Drilling / samples**; these literal observations are
retained in the log and field tables. Normalized SPT results belong to their
separate calculation worksheet and do not overwrite the original observations.

Expand **Engineering > Calculations** to browse methods by family, or use the
task search. A calculation has one editor, reached from either location. **Save
case** retains its inputs in the project; calculated results are recomputed.

For a combined PDF, choose **Report setup > Complete field report** and check
the saved calculation worksheets and slope cases to append (up to 20 in total). Select cases relevant to
this borehole and load scenario. Borehole logs, field data, selected originals
and the existing geological-section pages are followed by the selected
engineering reports, with PDF bookmarks. Calculations are recomputed in the
background. An incomplete case or missing engine prevents the combined export
and identifies the affected case; it is not silently omitted. The PDF keeps the
page layouts of each report, including landscape calculation sheets.

Apply field-editor changes and save calculation cases before export. Preview
and export use identical prepared bytes. The annex selection is for the current
session and borehole; select it again after opening a project or changing
boreholes. Portable report profiles retain layout choices, not project case
names. Selected circular-slope cases use the same isolated local engine as the
slope workspace, including source checks, method warnings and input fingerprints.
Large search cases take longer; the interface remains available while preparing
the combined document. Individual calculation and slope PDF exports remain available.

Review all log intervals, descriptions, samples, SPT observations, recovery,
RQD, water levels and units before exporting. In **Geological sections**, use
**Depth comparison** for column comparison or **Spatial section** with appropriate
coordinates and elevations. Review borehole ordering and interpreted contacts,
save the section and export it to PDF.

For an existing scanned section, choose **Interpreted contacts > Digitize scanned
section...** in a spatial section. Open the image or PDF, select the page, pick
upper-left and lower-right grid references and enter their station/elevation in
metres. Pick contact vertices, add them for review, then review and save the
section. Use an axis-aligned scan and the same station origin and elevation datum
as your section. Keep the original document with your project files. See the
[section workflow](GEOLOGICAL_SECTIONS.md#digitize-a-scanned-section).

**Source image** displays the calibrated preview saved with the project.
**Interpreted units** defines colored and patterned units between named contacts;
crossings and overlaps are rejected. Use **Unit colors / patterns** to compare
the fills with the reference image. Review and save the chosen display before
exporting; the same settings apply to the section PDF/SVG and full report.

Check every exported page for content, units, scale, clipping and pagination.
Interpretations must be distinguished from observed data. A PDF is an output,
not an editable project backup. When printing logs, use the appropriate actual-size
setting and check the scale on the printed output.

Specialist calculation tools require suitable parameters, units, groundwater
conditions and method assumptions. Check the selected method and its documented
domain before using a result in an engineering assessment.

## 6. Save recovery and updates

Saving a changed, valid project keeps one previous revision as
`<project>.boreholedesk.json.bak`. Saving unchanged data does not rotate it away.
If backup creation or replacement fails, the existing project is preserved.

**File > Recover previous save** opens the selected backup as an unsaved project.
Choose a new destination when saving and compare revisions before replacing
anything. If a project is damaged, use **Save as** with another name; do not
overwrite the damaged file or its backup while diagnosing the problem.

The backup retains one previous saved revision. Apply and save edits regularly.
On close, **Save** stores applied data. Unapplied drafts must be
applied or explicitly discarded. Canceling the close or a failed save keeps work open.
Keep external copies of your projects and backups.

Close the program before updating and use the new version's installer. Personal
UserData files and projects outside the program folder are preserved on upgrade
and uninstall. To repair missing or damaged components, rerun the matching
installer; verified model files are reused. Do not delete UserData to repair a reader.

## 7. Support and diagnostic reports

**Help > Export diagnostic report** creates a local JSON file with versions and
the current workspace and calculation-method identifier, and blank
reproduction/expected/observed fields. Add the shortest sequence of steps that
reproduces the problem, what you expected and what actually happened in those
fields before sharing the file. It does not contain project data,
paths, credentials or environment values, and is not sent automatically. Review
attachments, remove confidential information, and include the installer version
and SHA-256 when reporting a problem. Prefer a minimal synthetic reproduction.

## 8. Calculation references

### Lateral profile load tests

In **Profile load tests**, the input panel has three steps:

1. **Measured data:** enter the tested profile's geometry and material, applied
   horizontal load, load/gauge heights and observed displacement. These data fit
   the soil response.
2. **Soil response:** choose the depth distribution, unsupported depth and
   spring spacing. The unsupported depth applies to both profiles.
3. **Profile to check:** enter the proposed profile, ground-level shear/moment
   and the adopted displacement limit. **Use tested profile properties** copies
   only length, width, inertia and material E; it preserves loads and the limit.

The proposed profile can match the tested one or differ from it. Switching steps
preserves entries. Complete all three before calculating. The displacement limit
is user-defined: 20, 25 and 30 mm are examples, not universal prescribed values.

### Method references

The **SPT - N60 and (N1)60** worksheet standardizes measured SPT blow counts
before applying correlations. Start with **SPT measurements**, then review
**Correction settings**. **Ground profile (optional)** supplies effective stress
from layers when direct effective stresses are unavailable. The worksheet
reports corrected blow counts; it does not directly calculate bearing resistance
or settlement. The graph in the Input guide is an illustrative example, not
results from an empty case.

The [complete module reference](MODULES.md) documents the calculation worksheets,
slope stability and field-to-report workflows, with inputs, equations and bibliography.

In **Slope stability > Model**, the **Ground** tool is selected for a new case.
Use the visible model toolbar to draw the ground or
water profile and edit the selected material contact. Click to add a point, drag
a handle to move it, or right-click a handle to remove it. Keep points ordered
from left to right. Select the material in **Layers** before editing its contact.
The coordinate tables update with each accepted edit and remain available for
exact input. **Inspect / pan**, the mouse wheel and **Fit image** control the view.
The **Required inputs** list identifies missing values and invalid surcharge
strips. Click an entry to open its input cell; required cells are highlighted.
No material properties or analysis circle are inferred from a drawn profile.
For surcharges, **Start X** and **End X** are horizontal positions, not heights.
End X must exceed Start X; arrows follow the ground surface over that strip.
In **Inspect / pan**, double-click a soil region, profile, surcharge, anchor or
slip-circle outline to open its existing input table. Selecting an element does
not change the model or its results. Anchor labels show the current calculated
force per metre and status on hover when a result is available.
**Expand model** hides the tables temporarily to give the diagram more space.
Prescribed-circle handles change its centre and radius; search handles change
the centre-search rectangle after ranges have been entered in **Search** (Circle search).
After an edit, choose **Calculate** to refresh the factor of safety and enable
PDF export. Geometry with missing inputs can be drawn as a draft; calculation
requires a complete model with compatible ground, contact and water extents.

For footing geometry, settlement load plans, earth pressures, SPT profiles,
pile profiles, lateral-test calibration and rock-slope orientations, open
**Input model** in the calculation workspace.
It updates from the current fields and tables even when **Auto calculate** is off.
Double-click a blue label or coloured layer to select its input field or table row.
In lateral-test calibration, the measured profile and the profile to check are
shown separately; selecting a label opens the corresponding input step.
Dense depth profiles retain all sample/reading markers and show spaced labels;
hover a marker for its details or select its full row in the table. Use zoom and
the expanded view to inspect a diagram in a smaller window.
This schematic shows the entered data; calculated diagrams and results remain in
their own tabs. Missing values stay blank and formulas remain as entered until
calculation. The input model is not included as a result in exported reports.

Lithology pattern selectors include a visual sample beside each material name.
In **Geological sections**, select a contact and enable **Move selected vertex**
to drag its handles in the preview. Coordinate tables remain available for exact
edits. **Escape** cancels a drag; vertices must remain within the section and
between their neighbours. Review and save the edited interpretation before
exporting. Observed borehole logs are retained independently of these contacts.

For **RMR 1989 - tunnels and mines**, use **RMR guide** to inspect ranges
and select observed categories. Enter measured strength, RQD and spacing in
their stated units. **Export RMR card PNG...** saves a 300 dpi classification
sheet with inputs, component ratings, rock class and the method reference.
Recalculate after editing inputs before exporting a PNG or calculation PDF.

RQD: Deere, D. U., and Deere, D. W. (1989), *Rock Quality Designation (RQD) after
Twenty Years*, Contract Report GL-89-1. The [official NTIS abstract](https://ntrl.ntis.gov/NTRL/dashboard/searchResults/titleDetail/ADA207597.xhtml)
supports sound pieces at least 100 mm long and measurement along the core axis.

Core recovery: FHWA (2006), *Soils and Foundations, Volume I*, FHWA NHI-06-088,
section 3.6.5.4, p. 3-44. [Manual](https://www.fhwa.dot.gov/engineering/geotech/pubs/nhi06088.pdf).

The [Methods and data checks page](https://github.com/javierloren/BoreholeDesk-downloads/blob/main/QUALITY.md)
provides the equations, variable definitions and supporting references. Specialist
calculation panels and reports identify their selected methods and bibliography.


### Slope loads and earthquake scenarios

Open **Slope stability > Loads / earthquake**. Add each vertical surcharge by
its start/end X coordinates and q in kPa per horizontal area. The model draws
the load above the ground; overlapping strips add. Enter the project's adopted
horizontal kh coefficient, or zero for static analysis. Inertia acts on soil
weight in the sliding direction; vertical acceleration and surcharge inertia
are not included. Calculate again after editing any action. Save the case
before selecting it as a report annex.

### Water on both faces of a wall

The layered active and layered at-rest worksheets accept an optional **Front
water depth below retained ground**. Both water depths use the retained-ground
surface as their datum. Blank means dry on that face. Front water is subtracted
from retained-side pressure without changing retained-soil effective stress.
Inspect the signed net diagram, force and base moment; a near-zero force may
still leave a couple, for which no resultant height is reported.

### Settlement versus time

Under **Footings**, choose **Primary consolidation - settlement versus time**.
Enter loads and compressible layers as in the stress/consolidation worksheet.
For each physical drainage layer, add cv in m2/day and 1 or 2 drained faces.
Enter elapsed days in **Times**, and the target average consolidation percentage
in **Parameters**. The layer details show drainage paths and characteristic
times; the main result gives the time to the settlement-weighted profile target.
Do not create fictitious drained interfaces by splitting a physical layer.

For additional long-term compression after an adopted practical primary
reference, choose **Secondary compression after primary reference**. Supply
the reference time, reference thickness/void ratio and measured void-ratio
index C_alpha for each layer. Times must be at or after the reference. This
worksheet reports additional secondary movement; it does not add primary or
instantaneous settlement. Both worksheets can be saved and appended to a
complete report. See [the method cards](modules/FOUNDATIONS.md#settlement_time).

## 9. Measured geophysical logs and field-test comparison


In **Calculations > Geophysics**, choose **Geophysical depth log / field-test
correlation**. Create one case for a named borehole/location, common measured-depth
reference and material domain; record these and the measurement provenance in
**Context**. Select the actual curve and unit: SP (mV), resistivity (ohm m), Vs/Vp
(m/s), gamma (API or counts/s), or temperature (degrees C).

Enter or paste **Readings**, or use **Import CSV / Excel...** for CSV, TSV or XLSX.
Select the sheet, depth and value columns, depth unit (m or ft), decimal separator
and any explicit NoData code. Values must already use the selected curve unit.
Depths must be strictly increasing or decreasing. Blank values are NoData, not zero.
Import replacement requires confirmation and preserves the source file.

For comparison, select one reference test/unit and enter reviewed comparison depths
and values in **Samples**: field N, N60, (N1)60, CPT qc (MPa), or UCS (MPa).
**Load saved SPT...** can copy the corresponding numeric results of a saved SPT
calculation; verify its borehole, depth datum and correction factors first. Original
handwritten/refusal records are not converted automatically. No reference samples
are required to view a measured log with **Compare measurements only**.

Set the maximum interpolation bracket. The schedule identifies exact, interpolated
and unmatched observations; explicit NoData and the log endpoints bound matching.
The depth figure and cross-plot show the selected observations. Optional linear or
power fits describe the supplied paired data within their observed reference range;
they do not automatically supply design parameters to another module. Use a
published, applicable engineering correlation separately when required.

Save the case with the project and export its calculation PDF. All readings remain
in the project; for logs longer than 40 rows the PDF input schedule shows the first
and last 20, while the plot uses all readings. This worksheet does not automatically
insert a curve into a borehole's stratigraphic column.
See the [method and bibliography](modules/FIELD_TESTS.md#geophysical).


### Digitize a plotted geophysical curve

In **Geophysics > Geophysical depth log / field-test correlation**, choose the
curve and its units first. On **Readings**, choose **Digitize image / PDF...**.
Open a straight, axis-aligned plot and select its source page. Pick the upper-left
and lower-right calibration corners, then enter the printed top/bottom depths
and left/right curve values. Choose metres or feet for source depths, and linear
or logarithmic values as printed. Reversed value scales are supported; logarithmic
limits must be positive. Confirm the same depth datum used by your field tests.

Pick readable curve points; use **NoData gap** for an obscured depth. No point is
extrapolated beyond the calibrated rectangle, automatically traced or resampled.
The existing geophysical comparison still uses its stated maximum interpolation
bracket; an explicit NoData row prevents bridging an unreadable stretch. Review
the trace and check the approval box before using the points. Replacing an
existing readings table requires confirmation.

The original is attached to the borehole. Reviewed picks keep its SHA-256, page
and pixel reference; calibration is recorded with the source. Existing saved
transcriptions are retained. Save the calculation case and project to preserve
the reviewed data. These are digitized plotted values with image/calibration
uncertainty, not new instrument measurements.

## 10. Foundation support movements and dynamic elastic properties

In **Calculations > Footings > Differential settlement and support rotation**,
enter support X/Y coordinates in metres and signed settlements in millimetres
(positive down). Add only the physical connections to assess, using the support
row numbers. Open **Input model** to inspect the plan and double-click a support
or connection to reach its input row. The optional project limit is entered as
the denominator N of 1/N. Optional adopted rigid-tilt gradients produce a separate
relative rotation; they do not change the uncorrected chord-limit comparison.
Settlements must come from measurement or a separate justified calculation.
Calculate, inspect the plan and rotation diagram, then save and export the PDF.

In **Calculations > Geophysics > Dynamic elastic moduli from Vp / Vs / density**,
enter co-located Vp and Vs in m/s and bulk mass density in kg/m3 at increasing
depths. Each row represents the same material and conditions. The schedule and
depth diagram give small-strain dynamic G, E, K, M in MPa and Poisson ratio.
These values are not automatically converted to static design moduli or applied
to a foundation worksheet. Both methods include contextual input references and
their equations in the [module reference](MODULES.md).

## 11. Rock-mass deformation modulus

In **Calculations > Rock mass properties**, select **Rock mass modulus -
Hoek-Diederichs 2006**. Enter reviewed GSI and disturbance D and confirm that
an effectively isotropic rock-mass model is applicable. Enter reliable intact Ei
in MPa for equation 4, or leave Ei blank explicitly to use simplified equation 2.
The input reference panel identifies the equation and parameter basis.

Calculate and review Erm in MPa, GPa and kPa and the sensitivity curves. Save the
case with the project or export its calculation PDF. The result is an empirical
rock-mass deformation estimate; it is not automatically assigned to an analysis.
Distinguish it from intact Ei, dynamic stiffness, constrained modulus M and subgrade
reaction k. See the [equations and reference](modules/ROCK.md#rock_modulus).


## 12. Rock-mass and joint strength

In **Calculations > Rock mass properties**, choose **Rock mass strength -
generalized Hoek-Brown** for a reviewed brittle, effectively isotropic rock mass.
Enter intact UCS (MPa), mi, GSI, D and the upper effective confinement. Review
the principal compression and Balmer shear envelopes. Equivalent c/phi are
explicitly the 2002 range fit with its reported bounds; they are not automatically
assigned to a slope case and do not provide a tensile constitutive law.

Choose **Joint peak strength - Barton JRC-JCS** for matching unfilled joint walls.
Enter JRC, JCS (MPa), residual friction (degrees) and normal stress/water pressure
states (MPa). Leave both block lengths blank for adopted field-scale parameters,
or supply both to apply the empirical block-size correction once. Nonpositive
effective normal stress receives no frictional contact resistance. Inspect peak
and residual-friction results separately. Save the case and export its calculation
PDF with the source schedule and references. These are strength worksheets, not
automatic block, wedge or global slope-stability calculations.
