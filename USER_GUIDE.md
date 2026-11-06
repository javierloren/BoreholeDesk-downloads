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

### Preview status and download safety

This preview is **not digitally signed**. Windows may display an unknown-publisher
or SmartScreen warning. Check the official source and published SHA-256; do not
disable system protection or install an unfamiliar root certificate to suppress warnings.
SHA-256 detects changed files; it does not establish publisher identity or certify
engineering results. Installation has been exercised on the development Windows
host with a normal user and restricted PATH. A clean Windows acceptance test is pending.

If a release is not publicly accessible yet, a complete local folder with Packages
can be used for testing. The EXE alone cannot fetch private or unpublished assets.
Older base ZIP previews do not include the local OCR/segmentation/slope engines.

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

Handwriting and whole-column readers are experimental. Their ability to produce
text is not evidence of correctness on every author's writing. Review every
proposed reading before adding it to a borehole or report. Engine confidence
values are not a calibrated probability that a geotechnical interpretation is correct.

## 4. Core photographs, recovery and RQD

### Manual reference example

In **Image RQD > Calculate manual RQD**, use a 100 cm drilled run and pieces of
60, 20, 10, 5 and 5 cm. Expected RQD is **90%**. The default policy includes pieces
**at least 10 cm long**. Four pieces of exactly 10 cm in a 60 cm drilled run give
**66.7%**, not zero. Recovery and RQD use the drilled run as their denominator;
combined results must be weighted by run length rather than averaging percentages.

### Photographic workflow

1. Choose **Local model (offline, trial)** and load a core-box photograph.
2. Calibrate the two physical ends of each visible row using a measured length.
   The author's reference boxes use **60 cm rows**. Measure other boxes; do not
   assume every row is 60 cm or stretch the visible rock extent to fill the row.
3. Mark and fix the depth blocks, then run **Process segmentation**.
4. Review solid/fractured regions, individual pieces, row assignments, scale,
   depth blocks and the actual drilled interval. Correct mistakes before calculating.
5. Calculate the reviewed intervals and explicitly save the runs to the borehole.
   Reopen the saved project and check the reported values.

Depth blocks remain part of the workflow. The apparent length of rock in a
photograph does not establish drilled run length or missing core. Fracture
interpretation and treatment of drilling-induced breaks require professional
judgment. Segmentation performance is not a measurement of final RQD accuracy.
Roboflow is used only if explicitly selected with the user's own configuration;
the local model does not use a shared author API key.

## 5. Logs, geological sections and reports

Review all log intervals, descriptions, samples, SPT observations, recovery,
RQD, water levels and units before exporting. In **Geological sections**, use
**Depth comparison** for column comparison or **Spatial section** with appropriate
coordinates and elevations. Review borehole ordering and interpreted contacts,
save the section and export it to PDF.

Check every exported page for content, units, scale, clipping and pagination.
Interpretations must be distinguished from observed data. A PDF is an output,
not an editable project backup. A successful export does not certify print scale
or replace independent review of geological or engineering conclusions.

Specialist calculation tools require suitable parameters, units, groundwater
conditions and method assumptions. Read their stated limitations. The preview
does not establish equivalence with a validated commercial design suite.

## 6. Save recovery and updates

Saving a changed, valid project keeps one previous revision as
`<project>.boreholedesk.json.bak`. Saving unchanged data does not rotate it away.
If backup creation or replacement fails, the existing project is preserved.

**File > Recover previous save** opens the selected backup as an unsaved project.
Choose a new destination when saving and compare revisions before replacing
anything. If a project is damaged, use **Save as** with another name; do not
overwrite the damaged file or its backup while diagnosing the problem.

This is one previous saved revision, not automatic saving of drafts or a complete
undo history. On close, **Save** stores applied data. Unapplied drafts must be
applied or explicitly discarded. Canceling the close or a failed save keeps work open.
Keep external copies of your projects and backups.

Close the program before updating and use the new version's installer. Personal
UserData files and projects outside the program folder are preserved on upgrade
and uninstall. To repair missing or damaged components, rerun the matching
installer; verified model files are reused. Do not delete UserData to repair a reader.

## 7. Record a tutorial and report problems

Use the installed Complete edition when demonstrating all readers offline.
Start with installation, then the synthetic example, a reviewed field sheet,
manual RQD, a calibrated core photograph, a section, save/reopen and PDF export.
Record the exact version and the installation choice. Show uncertain readings
and their correction, not just a successful result. Use only material you may share.

**Help > Export diagnostic report** creates a local JSON file with versions and
blank reproduction/expected/observed fields. It does not contain project data,
paths, credentials or environment values, and is not sent automatically. Review
attachments, remove confidential information, and include the installer version
and SHA-256 when reporting a problem. Prefer a minimal synthetic reproduction.

Public preview feedback and independent professional acceptance are different
milestones. The former helps improve the product; it does not imply the latter.
