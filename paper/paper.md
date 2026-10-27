---
title: 'MRI Reconstruction from k-space to Deep Learning: A Hands-on Introduction'
tags:
  - MRI
  - image reconstruction
  - compressed sensing
  - deep learning
  - medical imaging
  - Jupyter notebooks
  - biomedical engineering
authors:
  - name: Anup Bagale
    orcid: 0009-0001-8261-7113
    affiliation: 1
affiliations:
  - name: Independent Researcher, Nepal
    index: 1
date: 27 October 2026
bibliography: paper.bib
---

# Summary

This learning module teaches how magnetic resonance imaging (MRI) scanners turn raw measurements into images, and how that process is accelerated with compressed sensing and deep learning. It consists of six Jupyter notebooks with exercises and worked solutions. Learners start from the two-dimensional Fourier transform and k-space, see how skipping k-space lines speeds up a scan and causes aliasing, implement compressed sensing reconstruction, train two neural networks, evaluate where all of these methods fail, and finally apply them to raw multi-coil data from a real scanner.

Every concept is introduced by computing it and looking at the result. All notebooks run in Google Colab with no installation. Notebooks 1–5 use simulated phantoms generated in code, so they need no data downloads and no data use agreements; Notebook 6 downloads openly licensed raw k-space from the M4Raw dataset [@Lyu2023]. The code is released under the MIT license and the text and figures under CC BY 4.0.

# Statement of need

Image reconstruction is a core topic of MRI and one of the most active areas of AI research in medical imaging. Learning it requires combining Fourier analysis, signal processing, optimization and deep learning, and seeing how these ideas interact on actual data. Students usually meet these topics in separate courses, and research papers assume all of them.

Hands-on material faces two practical barriers. First, the large public raw-data collections used in research, such as fastMRI [@Zbontar2018], require an application and a data use agreement, which is difficult for self-learners and for students without an institutional affiliation. Second, research code and toolboxes are written for people who already understand the methods, not for building that understanding step by step.

This module fills that gap with a single, open sequence that goes from Fourier basics to deep learning reconstruction in small, runnable steps, on free hardware. It also gives explicit attention to evaluation: published work has shown that learned reconstructions can be unstable, lose small structures, or add features that are not there [@Antun2020; @Muckley2021], and the module lets learners reproduce such failures themselves.

The target audience is final-year undergraduate and early graduate students in biomedical engineering, physics, electrical engineering and computer science, instructors of medical imaging courses, and self-learners. Because Notebook 6 uses data from an affordable low-field (0.3 T) scanner [@Lyu2023], the module is also relevant to learners in regions where such systems are being adopted.

# Learning objectives

After completing the module, learners will be able to:

1. Explain how an MRI scanner samples k-space and how the inverse Fourier transform produces an image.
2. Predict the artifacts produced by different undersampling patterns, using the point spread function.
3. Implement compressed sensing reconstruction with iterative soft thresholding (ISTA) and choose its regularization weight.
4. Train a U-Net and an unrolled network with data consistency for accelerated reconstruction.
5. Evaluate reconstructions with NRMSE, PSNR and SSIM, and explain why these measures can disagree with each other and with diagnostic quality.
6. Recognize distribution shift and test whether a method keeps small or unfamiliar structures.
7. Load raw multi-coil k-space, combine coil images, and apply the methods above to real scanner data.

# Content

| Notebook | Topic | Key activities |
| --- | --- | --- |
| 1 | Images and k-space | Centered FFT; each k-space point as a stripe pattern; center vs edges of k-space; resolution; spike artifacts |
| 2 | Undersampling and aliasing | Acceleration factor; regular, random and variable-density sampling; point spread function; why noise-like artifacts can be removed |
| 3 | Compressed sensing | Compressed sensing for MRI [@Lustig2007]; sparsity in a Haar wavelet basis; soft thresholding; ISTA [@Daubechies2004]; effect of the regularization weight |
| 4 | Deep learning reconstruction | Simulated training data; a U-Net [@Ronneberger2015]; an unrolled network with data consistency [@Schlemper2018; @Hammernik2018]; accuracy and speed |
| 5 | Evaluation and pitfalls | NRMSE, PSNR and SSIM [@Wang2004]; features absent from training [@Antun2020]; new masks, higher acceleration and noise [@Knoll2019]; images unlike the training data |
| 6 | Real scanner data | Multi-coil k-space from M4Raw; coil combination; zero-padded acquisitions; training and testing on separate subjects |

Each notebook ends with four exercises; learners in the pilot needed about one to three hours per notebook on their own. The results are concrete and reproducible. In Notebook 3, compressed sensing roughly halves the zero-filled error on the Shepp-Logan phantom [@Shepp1974] from the same 64 measured k-space lines. In Notebook 4, an unrolled network reaches about a sixth of the zero-filled error on simulated test phantoms, with 16 times fewer weights than the U-Net. Yet in Notebook 5, on a photograph, both networks do worse than no reconstruction at all, while compressed sensing still helps. On real low-field data in Notebook 6, the phantom-trained U-Net does worse than zero-filling, the phantom-trained unrolled network still helps because data consistency anchors it to the measurements, and a network trained for about a minute on real data performs best.

The notebooks use NumPy [@Harris2020], Matplotlib [@Hunter2007], scikit-image [@vanderWalt2014] and PyTorch [@Paszke2019]. Shared helper functions are introduced once and reused, so code from earlier notebooks stays familiar.

# Prerequisites

Learners need basic Python and NumPy, complex numbers, and an introductory understanding of the Fourier transform. No prior knowledge of MRI or deep learning is assumed; Notebook 4 introduces the necessary PyTorch.

# Instructional design

Every experiment is preceded by a prediction question. Learners write down what they expect before running the cell, then compare. Asking students to predict before observing a demonstration improves what they learn from it [@Crouch2004], and wrong predictions mark exactly the ideas that need discussion.

Each notebook follows the same pattern: learning objectives, a short explanation, a runnable experiment, an interpretation, exercises with hints, and a summary with references. Data are small and generated in code, so every experiment runs in seconds to minutes on a free Colab session, all random seeds are fixed, and every learner sees the same results.

The module deliberately includes experiments where methods fail: ghost copies that no algorithm can remove, a regularization weight that merges small structures, a network that erases a feature it never saw in training, and networks that perform worse than zero-filling on unfamiliar images. These failures build the critical judgement needed to read research on AI reconstruction, and Notebook 5 ends with a checklist for evaluating such claims.

An instructor guide in the repository gives timing, suggested workshop and course formats, and common difficulties.

# Experience of use

The notebooks were developed and tested in Google Colab, on CPU runtimes and on free T4 GPU runtimes. Every notebook was run from top to bottom in a fresh session before release, and Notebook 6 was run end to end on the real M4Raw data; its interpretations are based on those results. All random seeds are fixed, so learners see the same numbers as the text, apart from small differences between CPU and GPU runs.

The module was then piloted with self-paced learners in October 2026. Seven students and recent graduates were invited to work through the notebooks on their own over about two weeks, in Google Colab, and to complete an anonymous feedback form; all agreed that their anonymous responses could be reported. All seven completed the form: two biomedical engineering students, four information technology students at bachelor's and master's level, and one participant from engineering. Six of the seven completed all six notebooks and one completed Notebook 1. All seven reported trying most of the exercises, and none reported errors running the code. Reported times ranged from about one hour for Notebook 1 to about three hours for Notebook 6.

On a scale from 1 to 5, participants' self-rated ability to explain k-space rose from a mean of 1.6 before the module to 4.6 after it, and their ability to explain why undersampling causes artifacts and how compressed sensing and deep learning remove them rose from 1.6 to 4.6. The clarity of the notebooks for self-study was rated 4.6 on average. Three participants named Notebook 5 as the most difficult, and one asked for more detailed explanations there. In response, Notebook 5 was extended with a roadmap of its questions, definitions of its key terms, a fuller explanation of how to read NRMSE, PSNR and SSIM, and a one-sentence summary after each result; the time estimates in all notebooks and in the instructor guide were also revised to the times participants reported. These results are self-reports from a small group, not a controlled evaluation, but they indicate that the module can be followed without an instructor.

# Story of the project

The author developed this module in 2026 while preparing for graduate study in biomedical engineering, with a research interest in the application of AI to medical imaging, and MRI reconstruction in particular. Learning the topic as an independent learner meant piecing together Fourier analysis from signal processing textbooks, compressed sensing from research papers, and deep learning reconstruction from code written for specialists, often without access to the large research datasets.

The module grew out of that path. Each notebook was built around a single question the author had needed to answer, such as why skipping k-space lines causes ghost copies, why random sampling makes artifacts removable, and why a network that performs well on its test set can still fail. The emphasis on evaluation reflects the author's view that anyone who builds AI methods for medical imaging must first learn how they fail. The final notebook uses openly licensed low-field data, connecting the material to affordable MRI systems that matter in regions such as the author's home country, Nepal.

# AI usage disclosure

Claude AI (Anthropic) assisted in the initial phase of this work by drafting the notebook text, code and paper. The author revised and verified all content, conducted the pilot study and takes full responsibility for the work.

# Acknowledgements

The author thanks the creators of the M4Raw dataset for releasing raw k-space data under an open license, and the developers of the open-source libraries used in this module.

# References
