# Instructor guide

This guide is for anyone who wants to teach with the module: in a course, a workshop, or a
reading group.

## Audience and prerequisites

The module is written for final-year undergraduate and early graduate students in biomedical
engineering, physics, electrical engineering or computer science. Learners need basic Python
and NumPy, complex numbers, and the idea of a Fourier transform. No prior MRI or deep learning
knowledge is assumed; Notebook 4 introduces the necessary PyTorch step by step.

## Sequence and timing

| Notebook | Topic | Time on your own | Runs on |
| --- | --- | --- | --- |
| 1 | Images and k-space | about 1 hour | any computer |
| 2 | Undersampling and aliasing | 1.5–2 hours | any computer |
| 3 | Compressed sensing | 1.5–2.5 hours | any computer |
| 4 | Deep learning reconstruction | 2–2.5 hours | GPU recommended (about 9 min of training on a CPU) |
| 5 | Evaluation and pitfalls | 2.5–3 hours | any computer |
| 6 | Real scanner data (M4Raw) | about 3 hours | GPU recommended; downloads about 300 MB |

These times are what learners reported in a self-paced pilot in October 2026, including the exercises. Plan more time than you expect for Notebooks 5 and 6.

Each notebook builds on the previous ones. Notebooks 1–3 can be taught as a stand-alone
introduction to MRI reconstruction; Notebooks 4–5 as an introduction to deep learning
reconstruction and its evaluation, for learners who already know k-space.

## Suggested formats

- **Two half-day workshops:** Notebooks 1–3 on the first day, 4–5 on the second. Notebook 6 as
  homework or a follow-up session.
- **Five or six weekly sessions** of about 2 hours, one notebook each.
- **Self-study:** every notebook explains its content fully and has worked solutions.

## Running the notebooks

The easiest option is Google Colab: the README has an "Open in Colab" button for each notebook,
and nothing needs to be installed. For Notebooks 4 and 6, ask learners to choose
*Runtime > Change runtime type > T4 GPU* before running. To run locally, install the packages
in `requirements.txt`.

If time is short in Notebook 4, set `USE_PRETRAINED = True` to download networks trained with
exactly the notebook's settings instead of training them. Notebook 5 always uses these weights.

## Teaching tips

- **Use the Predict questions.** Before each experiment, the notebook asks learners to predict
  the result. Ask them to write down or share their prediction before running the cell, then
  discuss the cases where the class was wrong. These are the most valuable moments.
- **Exercises** come with hints. Full solutions, with outputs, are in `solutions/`; share them
  after the session if learners should try the exercises first.
- **Common difficulties:** the difference between frequency and phase encoding (Notebooks 1–2),
  why random sampling helps (Notebook 2, Section 7), and why a lower error does not always mean
  a better image (Notebooks 4–5). In the pilot, learners found Notebook 5 the most difficult; its
  opening roadmap and the short "In short" summaries after each result are good points to pause
  and discuss.
- **Results are reproducible:** all notebooks use fixed random seeds, so every learner should
  see the same numbers, apart from tiny differences between CPU and GPU in Notebooks 4 and 6.

## Collecting feedback

A short anonymous form after each session is enough: prior knowledge, which parts were clear or
confusing, time needed, and a before/after self-rating on each learning objective.
