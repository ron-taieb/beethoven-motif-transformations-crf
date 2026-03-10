# Probabilistic Multilabel Graphical Modelling of Motif Transformations in Symbolic Music

## Associated Paper

This repository accompanies the paper:

**Taieb, R., Greenberg, Y., & Sober, B.**
*Probabilistic Multilabel Graphical Modelling of Motif Transformations in Symbolic Music.*

Department of Statistics and Data Science and Department of Musicology,
The Hebrew University of Jerusalem, Jerusalem, Israel.

This repository provides the code and processed dataset used to construct the motif transformation dataset and perform the CRF-based statistical analysis described in the paper.

If you use this repository, please cite:

```
@article{taieb2026motif_crf,
  author  = {Taieb, Ron and Greenberg, Yoel and Sober, Barak},
  title   = {Probabilistic Multilabel Graphical Modelling of Motif Transformations in Symbolic Music},
  year    = {2026}
}
```

---

# Overview

This repository contains the code and processed data used for the statistical analysis of motif transformations in Beethoven piano sonatas using a multilabel Conditional Random Field (CRF) model.

The project integrates symbolic score representations from the **BPSD dataset** with motif annotations from **BPS-Motif** in order to construct a motif-level dataset describing musical transformations.

The repository includes the scripts used to construct the dataset as well as the final dataset used in the CRF analysis.

The goal of the analysis is to study the statistical relationships between transformation families (e.g., contour preservation, rhythmic variation, symmetry, etc.) within segments of Beethoven sonatas.

---

# External Datasets

This work builds on two publicly available datasets.

## BPS-Motif (motif annotations)

Hsiao et al. (2023)
*BPS-Motif: A dataset for repeated pattern discovery of polyphonic symbolic music*
Proceedings of the 24th International Society for Music Information Retrieval Conference (ISMIR).

Repository:
[https://github.com/Wiilly07/Beethoven_motif](https://github.com/Wiilly07/Beethoven_motif)

This dataset provides motif annotations for Beethoven piano sonatas.

---

## BPSD (symbolic score representation)

Zeitler et al. (2024)
*BPSD: A Coherent Multi-Version Dataset for Analyzing the First Movements of Beethoven's Piano Sonatas*
Transactions of the International Society for Music Information Retrieval.

Dataset used in this work: **BPSD Version 2**

Dataset archive:
[https://zenodo.org/records/12783403](https://zenodo.org/records/12783403)

The BPSD dataset provides structured symbolic score representations which are used to derive musical features and contextual information for each motif.

---

# Final Dataset

The dataset provided in `transformations_with_motifs/` contains:

* motif-level musical features
* segment-level metadata
* multilabel transformation annotations

Each motif instance is labeled with transformation families relative to an anchor motif within the same motif group.

This dataset is the final processed representation used in the CRF analysis.

---

# Repository Structure

```
build_bps_full_representation.ipynb
    Builds the symbolic representation derived from the BPSD dataset.

clean_csv_ann.ipynb
    Cleans and standardizes motif annotations from the BPS-Motif dataset.

build_motif_transformation_dataset.ipynb
    Constructs motif-level features and transformation labels by aligning
    BPSD representations with BPS-Motif annotations.

data_preprocessing.ipynb
    Additional preprocessing utilities used in constructing the dataset.

fix_sonata_25_bps_motif.ipynb
    Special preprocessing for Sonata 25. Its motif representation is derived
    from the same BPS-Motif repository but required a slightly different
    processing pipeline to match the structure used for the other sonatas.

crf_motif_transformation_analysis.ipynb
    Main analysis notebook. Fits the CRF model and performs statistical
    inference including Wald confidence intervals, likelihood ratio tests,
    and permutation tests.

transformations_with_motifs/
    Final dataset used for the CRF analysis.
```

---

# Data Processing Pipeline

The dataset used for the CRF model is constructed through the following steps:

1. **Symbolic score processing**
   The BPSD dataset is used to build a consistent symbolic representation of the Beethoven sonatas.

2. **Motif annotation processing**
   Motif annotations from the BPS-Motif dataset are cleaned and standardized.

3. **Motif alignment**
   Motif annotations are aligned with the symbolic score representation.

4. **Feature extraction**
   Musical features are computed for each motif, including contextual and harmonic descriptors.

5. **Transformation labeling**
   Each motif instance is labeled with transformation families relative to an anchor motif within the same motif group.

6. **Dataset construction**
   Motif features, metadata, and transformation labels are combined to form the final dataset used in the CRF analysis.

---

# Quick Start

To reproduce the analysis:

1. Clone the repository
2. Open

```
crf_motif_transformation_analysis.ipynb
```

3. Run all cells

The notebook loads the processed dataset located in:

```
transformations_with_motifs/
```

and reproduces the statistical analysis presented in the study.

---

# Reproducibility

The repository includes:

* all scripts used to construct the motif transformation dataset
* the final processed dataset used in the analysis
* the notebook containing the full CRF modeling pipeline and statistical inference

The original datasets (**BPSD** and **BPS-Motif**) are not redistributed here. Instead, links to the official sources are provided above together with the scripts required to reproduce the preprocessing pipeline.

---

# License and Attribution

The external datasets used in this work remain subject to their respective licenses. Please refer to the original dataset repositories for licensing details.

If you use the datasets, please cite the original works:

```
@inproceedings{Hsiao2023,
  author    = {Hsiao, Yi-Wei and Hung, Tsung-Yu and Chen, Tien-Ping and Su, Li},
  year      = {2023},
  title     = {BPS-Motif: A dataset for repeated pattern discovery of polyphonic symbolic music},
  booktitle = {Proceedings of the 24th International Society for Music Information Retrieval Conference (ISMIR)},
  pages     = {281--288}
}
```

```
@article{Zeitler2024,
  author  = {Zeitler, Johannes and Wei{\ss}, Christof and Arifi-M{\"u}ller, Vlora and M{\"u}ller, Meinard},
  year    = {2024},
  title   = {BPSD: A Coherent Multi-Version Dataset for Analyzing the First Movements of Beethoven's Piano Sonatas},
  journal = {Transactions of the International Society for Music Information Retrieval},
  volume  = {7},
  number  = {1},
  pages   = {195--212}
}
```


