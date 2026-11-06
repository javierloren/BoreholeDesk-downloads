# BoreholeDesk 0.1.3: third-party components and source access

BoreholeDesk's application code is distributed under GNU AGPL version 3.
Third-party components retain their own copyrights and licences. Full licence
texts supplied by the installed distributions accompany the application in
`Licenses` and the component runtimes' `.dist-info` directories. `Components/manifest.json`
records exact package versions and file hashes for the local engines.

## Desktop and document components

- **CPython 3.12.6**: Python licence; the embedded runtime and licence text are included.
- **Qt 6.12.0, PySide6 Essentials and Shiboken 6.12.0**: Qt open-source terms,
  including LGPLv3/GPLv3 as applicable to the supplied libraries. See the full
  GPL/LGPL texts under `Licenses/Qt` and the version-matched source links below.
- **pypdfium2/PDFium**: upstream PDFium and dependency notices accompany the wheel.
- **Pillow-HEIF 1.8.1**: BSD-3-Clause for its Python source. Its binary distribution
  includes libheif 1.23.6 and libde265 1.1.3 under LGPLv3, x265 4.3 under GPLv2 or
  later, and MinGW runtime components with their respective exceptions/notices.
  The original `LICENSES_bundled.txt` is retained. x265's upstream source grants
  the option of a later GPL version; its licence is not replaced by BoreholeDesk's.
- **PyInstaller**: its bootloader exception permits generated applications to
  be distributed under their applicable licences. The original notice is retained.

## Local engines and models

- **RapidOCR 3.9.2 / ONNX Runtime**: their notices and recorded OCR model provenance
  are included. PaddleOCR-derived model sources are recorded in `MODEL_SOURCES.json`.
- **RF-DETR 1.4.3**: Apache-2.0. The local RQD pack records the selected model hash
  and its training provenance.
- **TrOCR / UniLM**: MIT source/base-model notices are retained with the general
  model and the Spanish adaptation. English/bilingual cursive mode uses the general model.
- **GLM-OCR**: upstream model card declares MIT; its original model card is retained.
- **XSLOPE 1.0.5**: Apache-2.0. Copyright 2025 Norman L. Jones. This product includes
  software developed by Norman L. Jones. Its `LICENSE.txt` and `NOTICE` are included.
- **PyAV 19.0.2 / FFmpeg 9.0.2**: PyAV Python bindings retain their BSD licence.
  Its binary wheel also supplies FFmpeg and codec libraries under their applicable
  GPL/LGPL terms. Preserve the codec licences when redistributing those binaries.
- **OpenCV**: the Python distribution's third-party notices cover its bundled
  dependencies, including its FFmpeg backend. The original notices are included.

The technical glossary is original BoreholeDesk content under the application
licence. Scientific method references are provided separately from these software
and model licence notices. A bibliographic citation does not replace permission
to redistribute third-party code, figures or publication text.

## Version-matched library source access

The following sources are provided by the upstream distributors. Download links
identify the versions used in this build; a source download is separate from
the normal end-user installation.

| Component | Source |
| --- | --- |
| Qt 6.12.0 | https://download.qt.io/archive/qt/6.12/6.12.0/single/qt-everywhere-src-6.12.0.tar.xz |
| PySide6 / Shiboken 6.12.0 | https://github.com/pyside/pyside-setup/archive/refs/tags/v6.12.0.tar.gz |
| Pillow-HEIF 1.8.1 | https://github.com/bigcat88/pillow_heif/archive/refs/tags/v1.8.1.tar.gz |
| libheif 1.23.6 | https://github.com/strukturag/libheif/archive/refs/tags/v1.23.6.tar.gz |
| libde265 1.1.3 | https://github.com/strukturag/libde265/archive/refs/tags/v1.1.3.tar.gz |
| x265 4.3 | https://github.com/Multicorewareinc/x265/archive/refs/tags/4.3.tar.gz |
| PyAV 19.0.2 | https://github.com/PyAV-Org/PyAV/tree/v19.0.2 |
| FFmpeg 9.0.2 | https://ffmpeg.org/releases/ffmpeg-9.0.2.tar.xz |
| PyAV FFmpeg build recipes | https://github.com/PyAV-Org/pyav-ffmpeg |
| OpenCV Python build recipes | https://github.com/opencv/opencv-python/tree/5.0.0.93 |
| OpenCV FFmpeg backend and notices | https://github.com/opencv/opencv_3rdparty/tree/ffmpeg/5.x |

The wheel licence directories and model cards contain additional upstream source
and copyright references. The repository's source-access page accompanies the
download page; contact the maintainer through the distribution repository's issue
tracker if a corresponding source link is unavailable.

## Replacing libraries and rebuilding

The supplied libraries are dynamically loaded. Close BoreholeDesk and work on a
copy of the installation. ABI-compatible replacement Qt libraries/bindings can
be built from the matching sources and substituted in `_internal/PySide6` and the
corresponding binding directories. Runtime packages can be replaced in their
component directories. The application's corresponding source/build scripts are
provided as `Corresponding-source.zip` for rebuilding the application with
modified libraries. No BoreholeDesk signing key is required for such a local build.

If a component file changes, update its entry in the editable component manifest
with the replacement file's size and SHA-256 when testing the modified installation;
the integrity checker otherwise identifies it as changed. Preserve required
copyright notices and licences when distributing a modified application or library.

Upstream references:
https://www.qt.io/development/open-source-lgpl-obligations
https://github.com/Multicorewareinc/x265/blob/4.3/source/x265.h
https://ffmpeg.org/legal.html
https://github.com/pyinstaller/pyinstaller/blob/develop/doc/license.rst
