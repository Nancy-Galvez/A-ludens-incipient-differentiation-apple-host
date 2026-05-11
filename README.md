# A-ludens-incipient-differentiation-apple-host
Authors: Daniel Cerqueda-García1*, Daniel Piñero2*, Helena S. Hernández-Rosales2,Nancy Gálvez-Reyes2, Martín Aluja1

1Red de Manejo Biorracional de Plagas y Vectores, Instituto de Ecología, AC–INECOL, Clúster Científico y Tecnológico BioMimic, Xalapa, Mexico.
2Departamento de Ecología Evolutiva, Instituto de Ecología, Universidad Nacional Autónoma de México, Mexico City, Mexico.

## Description

The Mexican fruit fly (*Anastrepha ludens*, Diptera: Tephritidae) is a highly polyphagous quarantine pest of citrus and mango. Recently, it has expanded from lowland tropical regions into highland temperate environments (>1,800 m a.s.l.) in Mexico, where it now infests commercially grown apples (*Malus domestica*), a novel host.

This repository contains **raw data and scripts** for a population genomics study aimed at understanding whether this expansion reflects:

- Host-driven genomic divergence (adaptation to apple), or
- A broader geographic process (range expansion into highlands)

We genotyped **261 flies** from **30 localities** and **10 host plants** across northeastern and east-central Mexico using SNP markers derived from GBS (genotyping-by-sequencing). Two SNP panels were analyzed (grouped by host or by locality) using PCA, PERMANOVA, Mantel tests, spatial–environmental partitioning, and genome scans.

## Key findings

- Genomic differentiation is **weak**, with extensive overlap among host-associated and locality-associated groups.
- **Locality explains more genomic variance than host**.
- The strongest signal is **isolation by distance**.
- **Latitude** explains the largest fraction of genomic variation; elevation contributes negligibly after variance partitioning.
- Host effects emerge **only in sympatric apple/non-apple localities** and remain modest.
- Genome scans recovered more locality-associated outliers; annotations highlight genes linked to chemosensation, signaling, membrane trafficking, and stress-related processes.

## Repository structure
a-ludens-apple-expansion-genomics/
├── README.md
├── environment.yaml # Conda environment with all dependencies
├── data/
│ ├── raw/ # Original GBS-derived SNP data (VCF, plink)
│ │ ├── host_panel.vcf
│ │ └── locality_panel.vcf
│ ├── metadata/
│ │ ├── localities.csv # Coordinates, elevation, host plant
│ │ └── sample_metadata.csv # Fly ID, locality, host, latitude, longitude
│ └── derived/ # Filtered datasets (optional)
├── scripts/
│ ├── 01_qc_filtering/
│ │ └── filter_snps.R
│ ├── 02_pca/
│ │ └── run_pca.R
│ ├── 03_permanova/
│ │ └── permanova_analysis.R
│ ├── 04_mantel_ibd/
│ │ └── mantel_ibd.R
│ ├── 05_variance_partitioning/
│ │ └── variance_partitioning.R
│ ├── 06_genome_scans/
│ │ ├── outlier_detection.R
│ │ └── annotation_enrichment.R
│ └── utils/
│ └── helpers.R
├── results/
│ ├── figures/ # PCA plots, maps, Manhattan plots
│ │ ├── pca_host.pdf
│ │ ├── pca_locality.pdf
│ │ ├── ibd_plot.pdf
│ │ └── outlier_manhattan.pdf
│ └── tables/ # PERMANOVA results, outlier lists
│ ├── permanova_results.csv
│ ├── outlier_snps.csv
│ └── annotation_summary.csv
└── manuscript/ # Optional: drafts, figures for paper
└── README.md

## Requirements

All analyses were performed in **R** (≥4.2) and **bash** (for VCF manipulation). Key R packages:

- `vcfR`, `adegenet`, `poppr` – SNP handling and diversity
- `vegan` – PERMANOVA, Mantel tests
- `psych`, `variancePartition` – variance partitioning
- `pcadapt`, `OutFLANK` – genome scans for outliers
- `ggplot2`, `ggpubr`, `maps` – visualization
- `tidyverse` – data manipulation

You can create the exact environment using the provided `environment.yaml`:

```bash
conda env create -f environment.yaml
conda activate a-ludens-popgen

Data availability
Raw GBS sequence data are available at [NCBI SRA under BioProject PRJNAXXXXXX] (pending). SNP matrices and metadata are provided in data/raw/ for reproducibility.
