# MRI Reconstruction from k-space to Deep Learning

A hands-on, open learning module that teaches how MRI images are reconstructed: from the Fourier transform and k-space, through undersampling and compressed sensing, to deep learning reconstruction and its pitfalls.

Every concept is introduced by computing it and looking at the result. All notebooks run in Google Colab with simulated data, so there is nothing to download and no data agreement to sign.

## Who it is for

Final-year undergraduate and early master's students in biomedical engineering, physics or computer science.

**Prerequisites:** basic Python and NumPy, complex numbers, and an introductory signals course (Fourier transform). No prior MRI or deep learning knowledge is needed.

## Notebooks

| # | Notebook | Status |
| --- | --- | --- |
| 1 | [Images and k-space](notebooks/01_images_and_kspace.ipynb) | Ready |
| 2 | [Undersampling and aliasing](notebooks/02_undersampling_and_aliasing.ipynb) | Ready |
| 3 | [Compressed sensing](notebooks/03_compressed_sensing.ipynb) | Ready |
| 4 | Deep learning reconstruction | In progress |
| 5 | Evaluation and pitfalls | Planned |
| 6 | Optional: real data with fastMRI | Planned |

Solutions to the exercises are in [`solutions/`](solutions/).

Open the notebooks in Google Colab:

- Notebook 1: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/01_images_and_kspace.ipynb)
- Notebook 2: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/02_undersampling_and_aliasing.ipynb)
- Notebook 3: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/anupbagale/mri-recon-tutorial/blob/main/notebooks/03_compressed_sensing.ipynb)

## Running locally

```bash
pip install -r requirements.txt
jupyter notebook
```

## License

- Code: [MIT License](LICENSE)
- Text and figures: [Creative Commons Attribution 4.0 (CC-BY 4.0)](https://creativecommons.org/licenses/by/4.0/)

## Author

Anup Bagale, Independent Researcher, Nepal
