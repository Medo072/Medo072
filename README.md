# Hi, I'm Mohamed

M.Sc. Computer Science student at the American University in Cairo, working on
AI-based ALS detection and HD-EMG motor unit decomposition for neuroprosthetic
control.

## What I'm working on

I work on decomposing high-density surface EMG into individual motor unit spike
trains — the signal layer under next-generation neuroprosthetic control. My main
project is **MUelim**, a decomposition algorithm built on extended-lag cospectral
matrices and approximate joint diagonalization (JADOC), written up for NeurIPS
submission. Around it I've built a validation harness that scores decomposition
against curated ground truth from multiple public datasets, and a GPU-batched
hybrid engine that pairs MUelim's fast AJD front-end with a convolution-kernel-
compensation refinement stage — reaching comparable recall to a cold-start CKC
decomposition at roughly 16x the speed.

A large part of the work is adversarial self-benchmarking: every claim is checked
against a stronger published baseline, and negative results are documented as
carefully as positive ones (46 experiment records and a standing "closed dead
ends" list). Honest positioning: a stronger published baseline (Swarm-Contrastive
Decomposition) currently leads on recall by roughly 1.5-1.8x, while this pipeline
runs 5-24x faster — speed is the defensible claim, recall is an open problem I'm
actively working to close.

**[MUelim →](#)** <!-- replace with repo link once public -->

### Technical highlights

- Decomposition pipeline: extend-lag → cospectral matrices → whitening →
  approximate joint diagonalization (JADOC) → silhouette gating → peel-off
  deflation
- GPU-batched refinement (CuPy/fp32) — batches ~90 independent filter
  refinements into single GEMMs
- Recall engineering on real curated data: +46% genuine motor units on one
  benchmark from fixing a single fixed-point convergence bug; +15% across four
  contraction levels on another
- Adaptive per-motor-unit filter tracking for dynamic (non-isometric)
  contractions
- Physiological accept gate based on discharge regularity (CoV-ISI) rather than
  recording-dependent SNR thresholds — transfers across datasets without
  retuning
- Benchmarked on DEMUSE, Hug/Avrillon, HYSER, and the MUnitQuest challenge,
  scored on both isometric and dynamic tasks
- Determinism engineered into the pipeline so single runs are trustworthy —
  I've retracted my own earlier results after multi-seed checks turned up
  inconsistencies

**Stack:** Python, NumPy, SciPy, scikit-learn, CuPy/CUDA, PyTorch, TensorFlow,
WFDB, MATLAB data interchange

## Background

- **Research Assistant**, American University in Cairo (Jan 2026–present) —
  early-stage ALS patient classification, transferring knowledge from mice EMG
  signals to the human spectrum with a custom AI model
- **Data Science Intern**, PayMob (Jul–Sep 2025) — migrated a merchant chatbot
  from a basic architecture to LangGraph agents; built an LLM-based Q&A system
  over monthly merchant performance reports with PDF ingestion and contextual
  retrieval; cut a parallelized HTML→PDF rendering pipeline's full-run time by
  ~97% (~4 hours → ~7 minutes)
- **Undergraduate Research Intern**, Stanford University (supervisor: Ahmad A.
  Rushdi, PhD) — demonstrated jailbreaking of vision-language models via
  frequency-domain adversarial attacks transferred to the image domain
- **B.Sc. Systems and Biomedical Engineering**, Cairo University (2021–2025,
  GPA 3.7/4.0) — graduation project on pancreatic cancer detection: deep
  learning lesion segmentation and radiomics feature extraction from CT/MRI

## Elsewhere

[LinkedIn](https://linkedin.com/in/mohamedii)
