# BoreholeDesk

Local desktop tools for reviewed geological and geotechnical field records, borehole logs and reports.

**[Download for Windows](https://github.com/javierloren/BoreholeDesk-downloads/releases/tag/v0.1.3-preview.2)** · [User guide](USER_GUIDE.md) · [Module reference](MODULES.md) · [RQD and data checks](QUALITY.md)

## Download and install

Choose **one** Windows installer from the [current release](https://github.com/javierloren/BoreholeDesk-downloads/releases/tag/v0.1.3-preview.2):

| Download | Recommended use | Total download |
| --- | --- | --- |
| **[Quick](https://github.com/javierloren/BoreholeDesk-downloads/releases/download/v0.1.3-preview.2/BoreholeDesk-0.1.3-preview.2-Quick-Windows-x64.exe)** | Start with projects, reports, calculations, printed OCR, local RQD and slopes | About **0.72 GB** |
| **[Complete](https://github.com/javierloren/BoreholeDesk-downloads/releases/download/v0.1.3-preview.2/BoreholeDesk-0.1.3-preview.2-Complete-Windows-x64.exe)** | Include all handwriting and whole-column readers before working offline | About **4.42 GB** |

Both initial EXEs are about 54 MiB. The installer downloads and verifies the
selected components automatically; the table shows the complete download, not
just the initial EXE. Follow the wizard and open BoreholeDesk from the Start menu.
Quick can be expanded later through **Help > Install local readers**.

No separate Python setup or shared Roboflow account is required. Both choices
use the same calculation methods and models. After installation, choose
**File > Open example project** or create your own project.

Use the Windows installer assets. GitHub's automatic **Source code** archives
contain repository files and are not Windows installers. See the
[User guide](USER_GUIDE.md) for the full installation and offline preparation workflow.

## Modules

- Projects, boreholes, lithology, samples, core recovery and RQD.
- Scanned field sheets and handwriting assistance with reviewed transcription.
- Core photographs, physical calibration, depth blocks and local RQD segmentation.
- Stratigraphic logs, geological sections, locations and data exchange.
- Shallow foundations: bearing resistance, contact pressures and settlement.
- Deep foundations: shaft/toe resistance, chart factors, groups and axial load transfer.
- Earth pressure: cohesive, Rankine, Coulomb, at-rest and layered calculations.
- Structural geology: stereonets, kinematic screens and explicit block geometry.
- Rock mass classification: RMR89, RMR14, SMR, quantified GSI and Q.
- Lateral profile tests, SPT reduction, electrical sounding and rigid pavement.
- Linear plane-strain finite elements and circular slope stability with active tiebacks.
- PDF/HTML reports, data checks and a starter EN/ES technical glossary.

The [module reference](MODULES.md) describes all **35 calculation worksheets**,
five slope methods and the field-to-report workflows, with equations, units,
input schedules, application conditions and bibliography.

## Working with field data

Review transcriptions beside the original field sheet, calibrate core photographs
using measured row lengths, confirm depth blocks and apply the reviewed data to
the borehole. The same project data support logs, sections and reports.

This preview is available for use and feedback. Windows can display an
unknown-publisher notice for this unsigned installer. Check the official download
source and published SHA-256; keep Windows security protections enabled.

## Licence and feedback

See [Licence and source code](LICENSING.md) for how AGPL applies to the application and your own data.

BoreholeDesk is distributed under AGPL-3.0. Corresponding source code and licence
notices are included with the application. Dependencies and models retain their
own licences. This repository hosts product downloads and user documentation.

Report the version, reproduction steps and expected/observed result. **Help > Export
diagnostic report** prepares a local file for review before sharing. Do not attach
confidential field documents, private photographs, credentials or personal data.
