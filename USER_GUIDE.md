# BoreholeDesk User Guide

BoreholeDesk is a desktop application for geological and geotechnical field
records, borehole logs, core photographs, interpretation and reports. This guide
describes the **0.1.3-preview.1 Windows x64 preview**. Public user documentation
is maintained in English; source documents may be in English or Spanish.

## 1. Download and install

1. Open the official release page and choose the version you want to test.
2. Download **BoreholeDesk-0.1.3-preview.1-setup.exe**. Do not use GitHub's
   **Code > Download ZIP** or **Source code** archives to install the application.
3. Run the installer. It installs for your current Windows user without requiring
   administrator rights, a separate Python installation or a Roboflow account.
4. Choose **Quick trial** or **Complete**, then follow the progress shown by the
   installer. It obtains and verifies the selected components automatically.
5. Open BoreholeDesk from the Start menu. Choose **File > Open example project**
   to explore fictitious data, or create a project of your own.

| Installation | Total download, including the installer | Local readers |
| --- | --- | --- |
| Quick trial | Approximately 0.72 GB | Printed/scanned OCR, photographic RQD and the slope engine are included; handwriting readers can be added later |
| Complete | Approximately 4.42 GB | All selected handwriting and whole-column readers are prepared for offline use |

The small EXE is the initial installer, not the total download. Both choices use
the same models and algorithms. No model is quantized to make Quick trial smaller.
Handwriting readers add approximately 1.77 GB; the advanced whole-column reader
adds approximately 1.93 GB. Selecting a missing reader offers a one-time guided
installation. **Help > Install local readers** installs the remaining readers.
After installation finishes, press **Read page(s)** again; your project stays open.

### Offline installation

Place the ten matching component ZIP/GZ assets in a **Packages** folder beside
the EXE, then run the installer. Do not extract, rename or mix component files
from different releases. The installer verifies and restores them itself.
Install all readers you will need before going to a site without internet access.
Keep the installer and matching packages if you want to repair the installation offline.

Windows 10/11 x64 is the target platform. For the complete edition, 16 GB of RAM
and 25 GB of free disk space are recommended for downloading, installing and
retaining the package. A GPU is not required. First use of a model can take longer
while its weights load into memory.

### Download checks

This preview is **not digitally signed**. Windows may display an unknown-publisher
or SmartScreen warning. Check the official source and published SHA-256; do not
disable system protection or install an unfamiliar root certificate to suppress warnings.
SHA-256 detects changed files; it does not establish publisher identity or certify
engineering results. Obtain the installer from the official release page and keep
it with its matching component assets when preparing for offline installation.

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

1. Use an empty borehole when testing a sheet that would overlap existing intervals.
2. In **Field sheets / OCR**, import a supported PDF or image.
3. Choose **Local OCR (RapidOCR)** for printed text or a handwriting reader for
   handwritten material. Select the appropriate document language.
4. Press **Read page(s)**. If a model is missing, accept its installation or
   cancel and continue with manual entry. Python setup is not required.
5. Compare the proposed transcription with the original, especially depths,
   sample identifiers, decimal separators, units and crossed-out notes.
6. Correct the text, then use **Prepare intervals** and **Apply and preview**
   only after reviewing the proposed structured data.

A depth description can be written as `5.00-5.40: Light brown clayey sand`.
Ambiguous writing must remain literal until reviewed: for example, **48-11**
must not automatically be interpreted as **48.11 m**. If no intervals are
recognized, review the transcription; do not assume report data were added.

Review the proposed text before adding it to a borehole or report. Reader confidence
helps prioritize review; approval of the depth, units and geological meaning comes
from comparison with the original field record.

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

Review all log intervals, descriptions, samples, SPT observations, recovery,
RQD, water levels and units before exporting. In **Geological sections**, use
**Depth comparison** for column comparison or **Spatial section** with appropriate
coordinates and elevations. Review borehole ordering and interpreted contacts,
save the section and export it to PDF.

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
blank reproduction/expected/observed fields. It does not contain project data,
paths, credentials or environment values, and is not sent automatically. Review
attachments, remove confidential information, and include the installer version
and SHA-256 when reporting a problem. Prefer a minimal synthetic reproduction.

## 8. Calculation references

The [complete module reference](MODULES.md) documents all 35 calculation worksheets,
slope stability and field-to-report workflows, with inputs, equations and bibliography.

RQD: Deere, D. U., and Deere, D. W. (1989), *Rock Quality Designation (RQD) after
Twenty Years*, Contract Report GL-89-1. The [official NTIS abstract](https://ntrl.ntis.gov/NTRL/dashboard/searchResults/titleDetail/ADA207597.xhtml)
supports sound pieces at least 100 mm long and measurement along the core axis.

Core recovery: FHWA (2006), *Soils and Foundations, Volume I*, FHWA NHI-06-088,
section 3.6.5.4, p. 3-44. [Manual](https://www.fhwa.dot.gov/engineering/geotech/pubs/nhi06088.pdf).

The [Methods and data checks page](https://github.com/javierloren/BoreholeDesk-downloads/blob/main/QUALITY.md)
provides the equations, variable definitions and supporting references. Specialist
calculation panels and reports identify their selected methods and bibliography.
