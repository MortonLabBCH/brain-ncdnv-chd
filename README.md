# Noncoding variants and sulcal patterns in congenital heart disease: Machine learning to predict functional impact
![MIT License](https://badgen.net/static/license/MIT/blue)
[![DOI](https://badgen.net/badge/DOI/10.1016%2Fj.isci.2024.111707)](https://doi.org/10.1016/j.isci.2024.111707)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14934079.svg)](https://doi.org/10.5281/zenodo.14934079)

### Overview

This repository contains the code used in the study: Mondragon-Estrada et al., [Noncoding variants and sulcal patterns in congenital heart disease: Machine learning to predict functional impact](https://www.cell.com/iscience/fulltext/S2589-0042(24)02934-1), iScience (2025), https://doi.org/10.1016/j.isci.2024.111707.

<p align="center">
    <img width=80% height=80% src="https://github.com/MortonLabBCH/brain-ncdnv-chd/blob/main/figures/graphical_abstract.png">
</p>

The main analyses were:

*   Variant score prediction using deep learning models
*   Statistical comparison of functional scores and quantitative traits
*   Functional score correlation with sulcal pattern features
*   Functional enrichment analysis in predicted target genes

A more detailed description of the methods is available in Mondragon-Estrada and Morton, [Protocol to analyze deep-learning-predicted functional scores for noncoding de novo variants and their correlation with complex brain traits](https://star-protocols.cell.com/protocols/4135), STAR Protocols (2025), https://doi.org/10.1016/j.xpro.2025.103738.

<p align="center">
    <img width=80% height=80% src="https://github.com/MortonLabBCH/brain-ncdnv-chd/blob/main/figures/graphical_abstract_2.png">
</p>

--------
### Requirements 

#### Hardware requirements
Deep learning predictions were carried out in GNU/Linux workstations with 128 GB of RAM and NVIDIA GPUs.

#### OS requirements 
Scripts were executed on `GNU/Linux Ubuntu 20.04.6 LTS (Focal Fossa)`. Deep learning models are implemented in `Python3` and their corresponding usage and requirements can be seen in their repositories. WGCNA and GO enrichment analysis were performed in `R 4.1.2`.

--------
### Setup and usage

Basenji2's predictions were obtained using the script [predict_scores_b.sh](https://github.com/MortonLabBCH/brain-ncdnv-chd/blob/main/scripts/predict_scores_b.sh). Instructions for installing Basenji2 and creating a conda environment are available in the original [Basenji2 GitHub repository](https://github.com/calico/basenji).

Enformer's predictions were obtained using the script [predict_scores_e.py](https://github.com/MortonLabBCH/brain-ncdnv-chd/blob/main/scripts/predict_scores_e.py). Instructions for installing Basenji2 and creating a virtual environment are available in the original [Enformer GitHub repository](https://github.com/google-deepmind/deepmind-research/tree/master/enformer).

For processing and statistical steps performed in Python3, we recommed creating a third virtual environment with this [requirements.txt](https://github.com/MortonLabBCH/brain-ncdnv-chd/blob/main/scripts/processing/requirements.txt).

```shell
    $ python3 -m venv venv
    $ source venv/bin/activate
    $ pip install -r requirements.txt
```
For analyses done in R, the following packages are required:

*   Bioconductor packages:
    *   WGCNA
    *   clusterProfiler
    *   biomaRt
    *   org.Hs.eg.db
    *   GenomicRanges
    *   ChIPpeakAnno
    *   TxDb.Hsapiens.UCSC.hg38.knownGene

*   CRAN packages:
    *   ggplot2
    *   dplyr
    *   RColorBrewer
    *   ppcor

They all can be installed using the following commands in R:

```R
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("WGCNA")
BiocManager::install("clusterProfiler")
BiocManager::install("biomaRt")
BiocManager::install("org.Hs.eg.db")
BiocManager::install("GenomicRanges")
BiocManager::install("ChIPpeakAnno")
BiocManager::install("TxDb.Hsapiens.UCSC.hg38.knownGene")

# For installing ggplot and dplyr, it is easier to install the whole tidyverse:
install.packages("tidyverse") 
# Alternatively, each package can be installed individually with the following commands:
install.packages("ggplot2")
install.packages("dplyr")

install.packages("RColorBrewer")
install.packages("ppcor")
```

--------
### Citations

```
@article{MONDRAGONESTRADA2025111707,
    author = {Enrique Mondragon-Estrada and Jane W. Newburger and Steven R. DePalma and Martina Brueckner and John Cleveland and Wendy K. Chung and Bruce D. Gelb and Elizabeth Goldmuntz and Donald J. Hagler and Hao Huang and Patrick McQuillen and Thomas A. Miller and Ashok Panigrahy and George A. Porter and Amy E. Roberts and Caitlin K. Rollins and Mark W. Russell and Martin Tristani-Firouzi and P. Ellen Grant and Kiho Im and Sarah U. Morton},
    title = {Noncoding variants and sulcal patterns in congenital heart disease: Machine learning to predict functional impact},
    journal = {iScience},
    volume = {28},
    number = {2},
    pages = {111707},
    year = {2025},
    issn = {2589-0042},
    doi = {https://doi.org/10.1016/j.isci.2024.111707},
    url = {https://www.sciencedirect.com/science/article/pii/S2589004224029341}
}
```

```
@article{MONDRAGONESTRADA2025103738,
    author = {Enrique Mondragon-Estrada and Sarah U. Morton},
    title = {Protocol to analyze deep-learning-predicted functional scores for noncoding de novo variants and their correlation with complex brain traits},
    journal = {STAR Protocols},
    volume = {6},
    number = {2},
    pages = {103738},
    year = {2025},
    issn = {2666-1667},
    doi = {https://doi.org/10.1016/j.xpro.2025.103738},
    url = {https://www.sciencedirect.com/science/article/pii/S2666166725001443},
}
```