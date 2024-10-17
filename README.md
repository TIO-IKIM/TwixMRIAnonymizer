# TwixMRIAnonymizer

[![Python 3.11.2](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12-blue)](https://www.python.org/downloads/release/python-3120/) 
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![DOI](https://img.shields.io/badge/DOI-j.cmpb.2023.107912-blue)](https://doi.org/10.48550/arXiv.2410.12402)

<div align="center">

[Getting started](#getting-started) • [Usage](#usage) • [Roadmap](#roadmap) • [Citation](#citation) • [Credits](#credits)

</div>

---

> **Update 17.10.2024**:
>
> :bangbang: The TwixMRIAnonymizer tool is now integrated in our new holistic de-identification tool. Check out the corresponding repository: https://github.com/code-lukas/medical_image_deidentification :bangbang:
>

---

**Twix MRI Anonymizer** is a lightweight Python anonymization-tool for Siemens MRI raw data format twix. 

Twix data contains multiple headers. while the dicom header, often saved as ['hdr'] is easily anonymizable, the much larger header ['hdr_string'] is often overlooked, but contains all the same information as the general header, as well as a detailed overview of the scan settings.

If anonymization is performed only on the first header, all the information contained in the latter will be pasted back into ['hdr'] when saving the "anonymized" file. 
This brings up the necessity and chances of the following code, which scans the ['hdr_string'] for all informations which need to be anonymized and additionaly can save useful metadata for further tasks.

While the main focus lies on the anonymization of MRI twix files, this tool also allows researchers to extract important metadata, such as sequence name, TR/TI and acceleration factor, for a large amount of data and saved in a csv overview.

## Getting started
1. Clone repository:
   
       git clone https://github.com/TIO-IKIM/TwixMRIAnonymizer.git

2. Create a conda environment with Python version 3.11.2 and install the necessary dependencies:
   
       conda env create -n anonymizer -f requirements.txt
    In case of installation issues with conda, use pip install -r requirements.txt to install the dependecies.

3. Activate your new environment:

       conda activate anonymizer

4. Run the script with the corresponding cli parameter, e.g.:

       python3 anonymize.py --i your/input/path --o your/output/path

Alternative pip installation from inside the repository folder:

       pip install -e .

## Usage
**Anonymization CLI**
```
usage: anonymize.py [-h] [--i I] [--o O] [--f] [--meta_only]

options:
  -h, --help   show this help message and exit
  --i I        The path to the TWIX file or directory containing TWIX files to be anonymized.
  --o O        The path to save the anonymized files.
  --f          If set, force overwrite existing files. Defaults to False
  --meta_only  If set, only save the metadata, but do not write anonymized file. Defaults to False
```

## Roadmap

#### Pip Package

Script will be wrapped into a package and published on pip.

## Citation

If you use our code in your work, please cite us with
```latex
@misc{rempe2024deidentificationmedicalimagingdata,
      title={De-Identification of Medical Imaging Data: A Comprehensive Tool for Ensuring Patient Privacy}, 
      author={Moritz Rempe and Lukas Heine and Constantin Seibold and Fabian Hörst and Jens Kleesiek},
      year={2024},
      eprint={2410.12402},
      archivePrefix={arXiv},
      primaryClass={eess.IV},
      url={https://arxiv.org/abs/2410.12402}, 
}
```

## Credits

Parts of the code of TwixAnonymizer is based on the great package [*Suspect*](https://suspect.readthedocs.io/en/#) by Ben Rowland, et al. for MRS processing.
