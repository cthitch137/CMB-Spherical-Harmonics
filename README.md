# CMB Angular Power Spectrum via Spherical Harmonics

A research notebook computing the **Cosmic Microwave Background (CMB) angular power spectrum** from scratch using spherical harmonic decomposition, applied to real data from the Planck satellite.

Written to be approachable for someone new to both the CMB and spherical harmonics — all math and physics is introduced from first principles before any code is shown.

---

## What This Notebook Does

1. Introduces the CMB and spherical harmonics conceptually
2. Visualizes spherical harmonic modes $Y_\ell^m(\theta, \phi)$ in 3D
3. Implements a simple $a_{\ell m}$ computation on fake data
4. Builds an optimized version using:
   - Stable normalized Legendre recurrence relations
   - Pre-computed complex exponentials
   - Numba JIT compilation for near-C speed
5. Loads the real Planck 2018 SMICA temperature map
6. Computes $C_\ell$ and compares to the official Planck power spectrum
7. Computes the two-point correlation function and cosmic variance bands
8. (Optional) Generates an animation of the CMB sky reconstruction mode-by-mode
9. (Optional) Estimates cosmological parameters from acoustic peak ratios

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/cmb-spherical-harmonics.git
cd cmb-spherical-harmonics
```

### 2. Set up the environment

**Option A — Conda (recommended):**
```bash
conda env create -f environment.yml
conda activate cmb-harmonics
```

**Option B — pip:**
```bash
pip install -r requirements.txt
```

### 3. Get the Planck data

The Planck SMICA map (~3 GB) is too large to store in this repository.
Download it and place it in the `data/` folder:

```bash
# The notebook will auto-download it for you when you run Section 6,
# or you can download manually from:
# https://irsa.ipac.caltech.edu/data/Planck/release_3/all-sky-maps/maps/component-maps/cmb/COM_CMB_IQU-smica_2048_R3.00_full.fits
```

> **Google Colab users:** Section 6.1 of the notebook includes a cell to mount
> Google Drive and save the file there, so you only download it once.

### 4. Run the notebook

```bash
jupyter notebook CMB_Spherical_Harmonics_Guide.ipynb
```

---

## Repository Structure

```
cmb-spherical-harmonics/
├── CMB_Spherical_Harmonics_Guide.ipynb   # Main notebook
├── requirements.txt                       # pip dependencies
├── environment.yml                        # Conda environment
├── README.md                              # This file
├── data/
│   └── .gitkeep                           # Place Planck .fits file here
└── .gitignore
```

---

## Dependencies

| Package | Purpose |
|---------|---------|
| `numpy` | Array math |
| `scipy` | Spherical harmonics, Legendre polynomials |
| `matplotlib` | Plotting |
| `healpy` | HEALPix sky maps (reading Planck data) |
| `astropy` | Reading FITS files |
| `numba` | JIT compilation for performance |
| `pandas` | Loading the official Planck power spectrum table |

---

## Background Reading

- Planck 2018 results: https://www.cosmos.esa.int/web/planck/publications
- CMB spectrum lecture notes (reference used throughout): https://cmb.wintherscoming.no/pdfs/AST5220_cmb_spectrum_2015.pdf
- HEALPix / healpy documentation: https://healpy.readthedocs.io

---

## License

MIT — see `LICENSE` for details.
