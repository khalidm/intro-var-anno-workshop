<style>
/* Wrap lines within the source code blocks */
pre.bash, pre.sh {
  white-space: pre-wrap !important;
}
/* Wrap lines within the command output blocks */
pre:not([class]) {
  white-space: pre-wrap !important;
}
</style>

---
title: Setup
---

Please follow the steps below and install the required software **before** the scheduled workshop.
<!--
FIXME: Setup instructions live in this document. Please specify the tools and
the data sets the Learner needs to have installed.

## Data Sets

FIXME: place any data you want learners to use in `episodes/data` and then use
       a relative link ( [data zip file](data/lesson-data.zip) ) to provide a
       link to it, replacing the example.com link.
Download the [data zip file](https://example.com/FIXME) and unzip it to your Desktop
-->

## Variant annotation data and tool setup

::::::::::::::::: checklist

### Dataset setup

This workshop utilzes a dataset of variants derived from \<insert details\>. The dataset, in [VCF](https://samtools.github.io/hts-specs/VCFv4.1.pdf) file format, contains genetic variants called in \<XX\> samples from chromosome \<XX\>.

[Click here for further information about the dataset](https://posit.co/download/rstudio-desktop/) and methods used to extract the VCF with regions of intereset is as follows:

```bash
tabix -h https://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/HGSVC3/release/Variant_Calls/1.0/GRCh38/vcf_with_unphased/variants_GRCh38_snv_snv_alt_with-unphased_HGSVC2024v1.0.vcf.gz chr22:20,000,000-20,100,000 > workshop_1000g_multi_sample.vcf
tabix -h tabix -h https://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/1000G_2504_high_coverage/working/20201028_3202_raw_GT_with_annot/20201028_CCDG_14151_B01_GRM_WGS_2020-08-05_chr2.recalibrated_variants.vcf.gz chr2:46,362,272-48,524,107 > workshop_1000g_multi_sample.vcf
```

This is a multi-sample VCF file containing variants from \<XX\> participants in the chromosome regions chr22:20,000,000-20,100,000.

::::::::::::::::::::::::::::

::::::::::::::::: checklist

### Tools setup

The workshop will use the ENSEMBL Variant Effect Predictor (VEP) tools. The instruction to install VEP are avalable [here](https://useast.ensembl.org/info/docs/tools/vep/script/vep_download.html). The website also provides a web interface to the application but for this workshop we will use the command line tool.

You can install packages from CRAN using:

```bash

# 1. Download
git clone https://github.com/Ensembl/ensembl-vep.git

# 2. Install
cd ensembl-vep
perl INSTALL.pl

# 3. Download and setup cache

cd $HOME/.vep
curl -O https://ftp.ensembl.org/pub/release-116/variation/indexed_vep_cache/homo_sapiens_vep_116_GRCh38.tar.gz
tar xzf homo_sapiens_vep_116_GRCh38.tar.gz

# 4. Test
./vep -i examples/homo_sapiens_GRCh38.vcf --cache


```

More details on the VEP command line tool and detailed instructions see the [documentation](https://useast.ensembl.org/info/docs/tools/vep/script/index.html). Most workshops using R will require the installation of specific packages. Make sure to check in advance with the workshop organisers what packages need to be installed.

::::::::::::::::::::::::::::

<!-- ## RStudio Setup

We use RStudio for coding in R.

[Click here and follow the instructions](https://posit.co/download/rstudio-desktop/) to install RStudio Desktop in your system.

::::::::::::::::: discussion

### R packages

Most workshops using R will require the installation of specific packages. Make sure to check in advance with the workshop organisers what packages need to be installed. 

You can install packages from CRAN using:

```r
install.packages("package_name")
```

If your package is in a different R repository, such as Bioconductor or GitHub, you may need the [BiocManager](https://www.bioconductor.org/install/) or [devtools](https://devtools.r-lib.org/) packages to install them. To install BiocManager:

```r
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install()
```

For devtools, you can simply do:

```r
install.packages("devtools")
```

You can then install packages directly from GitHub with:

```r
devtools::install_github("username/reponame")
```

::::::::::::::::::::::::::::
 -->

<!--
READ HERE FOR OS-SPECIFIC INSTRUCTIONS

Setup for different systems can be presented in dropdown menus via a `spoiler`
tag. They will join to this discussion block, so you can give a general overview
of the software used in this lesson here and fill out the individual operating
systems (and potentially add more, e.g. online setup) in the solutions blocks.
-->

<!--
:::::::::::::::: spoiler

### Windows

Use PuTTY

::::::::::::::::::::::::

:::::::::::::::: spoiler

### MacOS

Use Terminal.app

::::::::::::::::::::::::


:::::::::::::::: spoiler

### Linux

Use Terminal

::::::::::::::::::::::::
-->

