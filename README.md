# MRI Reconstruction from k-space to Deep Learning

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23695724.svg)](https://doi.org/10.5281/zenodo.23695724)

A hands-on, open learning module that teaches how MRI images are reconstructed: from the Fourier transform and k-space, through undersampling and compressed sensing, to deep learning reconstruction, its pitfalls, and real scanner data.

Every concept is introduced by computing it and looking at the result. All notebooks run in Google Colab. Notebooks 1–5 use simulated phantoms, so there is nothing to download and no data agreement to sign; Notebook 6 downloads openly licensed raw MRI data.

## Who it is for

Final-year undergraduate and early graduate students in biomedical engineering, physics, electrical engineering or computer science, and instructors who want to teach MRI reconstruction with code.

**Prerequisites:** basic Python and NumPy, complex numbers, and an introductory signals course (Fourier transform). No prior MRI or deep learning knowledge is needed.

## Notebooks

| # | Notebook | Topics |
| --- | --- | --- |
| 1 | [Images and k-space](notebooks/01_images_and_kspace.ipynb) | 2D Fourier transform, k-space, resolution, spike artifacts |
| 2 | [Undersampling and aliasing](notebooks/02_undersampling_and_aliasing.ipynb) | Acceleration, regular vs random sampling, point spread function |
| 3 | [Compressed sensing](notebooks/03_compressed_sensing.ipynb) | Sparsity, Haar wavelets, soft thresholding, ISTA, choosing λ |
| 4 | [Deep learning reconstruction](notebooks/04_deep_learning_reconstruction.ipynb) | Training data, U-Net, unrolled network with data consistency |
| 5 | [Evaluation and pitfalls](notebooks/05_evaluation_and_pitfalls.ipynb) | NRMSE, PSNR, SSIM, small features, distribution shift |
| 6 | [Real scanner data (M4Raw)](notebooks/06_real_data_m4raw.ipynb) | Multi-coil k-space, coil combination, training on real data |

Open the notebooks in Google Colab:

- Notebook 1: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/01_images_and_kspace.ipynb)
- Notebook 2: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/02_undersampling_and_aliasing.ipynb)
- Notebook 3: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/03_compressed_sensing.ipynb)
- Notebook 4: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/04_deep_learning_reconstruction.ipynb)
- Notebook 5: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/05_evaluation_and_pitfalls.ipynb)
- Notebook 6: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/06_real_data_m4raw.ipynb)

## How to use this module

**As a learner:** work through the notebooks in order. Each one starts with its learning objectives, asks you to predict the result before every experiment, and ends with exercises. Worked solutions, with outputs, are in [`solutions/`](solutions/).

**As an instructor:** see the [instructor guide](INSTRUCTOR_GUIDE.md) for timing, suggested course and workshop formats, and teaching tips. The [`weights/`](weights/) folder holds the networks trained in Notebook 4, so a class can skip training if time is short.

## Running locally

```bash
pip install -r requirements.txt
jupyter notebook
```

## Data

Notebooks 1–5 use simulated phantoms only. Notebook 6 downloads real k-space data from the M4Raw dataset ([Lyu et al., 2023](https://doi.org/10.1038/s41597-023-02181-4)), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) and hosted at [huggingface.co/datasets/mylyu/M4Raw_brain](https://huggingface.co/datasets/mylyu/M4Raw_brain). No data is stored in this repository.

## Contributing and support

Questions, problem reports and improvements are welcome. Please open an [issue](https://github.com/anupbagale/mri-recon-tutorial/issues) or see [CONTRIBUTING.md](CONTRIBUTING.md).

## License

- Code: [MIT License](LICENSE)
- Text and figures: [Creative Commons Attribution 4.0 International](LICENSE-CC-BY-4.0.txt)

## Citation

If you use this module in teaching or research, please cite it:

> Bagale, A. (2026). *MRI Reconstruction from k-space to Deep Learning: A Hands-on Introduction* (Version 1.0.1) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.23695724

The same information is in [CITATION.cff](CITATION.cff) and the "Cite this repository" button on GitHub.

## Author

Anup Bagale, Independent Researcher, Nepal
